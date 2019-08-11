---
layout: post
title: "Visual Studio Code Breakpoints for Angular Multi-Project Workspace"
date: 2019-08-11
---
### Unverified breakpoints everywhere
Recently I've been using Visual Studio Code as my Angular IDE. I also started playing around with the relatively new [multi-project workspace organization structure](https://angular.io/guide/file-structure#multiple-projects) available in more recent versions of Angular. But after creating my first project within my new workspace, I couldn't quite figure out how to get VS Code to recognize my breakpoints.

As is typical with development setup questions, the answer is quite obvious in retrospect, a combination of simple steps. If only the question had been asked and answered verbatim on Stack Overflow...

### Solution: adjust your source maps
I'm assuming you've already installed the ["Debugger for Chrome" extension for VS Code](https://code.visualstudio.com/blogs/2016/02/23/introducing-chrome-debugger-for-vs-code) and generated a workspace application sub-project using the Angular CLI e.g. `ng generate application new-app`.

The Node debugger in VS Code sometimes requires additional information in order to understand how source code gets mapped to transpiled application code, which is used when setting IDE debug points in code that you've actually written. This involves [adding/editing the `sourceMaps` field of a `configurations` entry](https://code.visualstudio.com/docs/nodejs/nodejs-debugging#_source-maps) in your project's `.vscode/launch.json` file.

Fortunately, [an answer to a GitHub issue](https://github.com/angular/angular-cli/issues/13154#issuecomment-445725373) provides a thorough explanation of the `sourceMaps` and `sourceMapPathOverrides` entries you'd want to add to the default "Launch Chrome against localhost":
```
"sourceMaps": true,
"sourceMapPathOverrides": {
    "/./*": "${webRoot}/*",
    "/src/*": "${webRoot}/*",
    "/*": "*",
    "/./~/*": "${webRoot}/node_modules/*",
}
```

To do this for a project in a multi-project workspace e.g. for an application project called `new-app` at the workspace repo's `projects/new-app` folder, you'd want to create an entry under the `configurations` array that looks like this:
```
{
    "name": "Launch new-app in Chrome against localhost (with sourcemaps)",
    "type": "chrome",
    "request": "launch",
    "url": "http://localhost:4200",
    "webRoot": "${workspaceRoot}",
    "sourceMaps": true,
    "sourceMapPathOverrides": {
        "/./*": "${webRoot}/projects/new-app/*",
        "/src/*": "${webRoot}/projects/new-app/src/*",
        "/*": "*",
        "/./~/*": "${webRoot}/node_modules/*",
    },
}
```

Very simple and obvious in retrospect, but it took me an hour more than it should have to piece these things together.

### Some notes
- Lazy-loading: if your project uses lazy-loading in its routing then **the breakpoint will be unverified until you actually navigate to the particular component in Chrome**. This is because the bundle which is getting mapped within the source map is not actually being served until it is lazy-loaded
- `workspaceRoot` refers to the folder path of the project that was opened as the workspace in VS Code
