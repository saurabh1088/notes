#  npm (Node Package Manager)


npm is package and dependency management tool for JavaScript and Node.js applications.
npm is a very crucial component in JavaScript ecosystem, it is used for :
- installing
- sharing
- & managing the libraries and packages used in JavaScript based projects.

*npm* comes bundled with *Node.js*
Hence to use *npm* one needs to have *Node.js* installed on system.

### Features/Functions of npm

- Installing Packages:

Using npm one can install third-party packages, libraries, and modules in Node.js
projects. Installed packages are stored in *npm registry*, a public repository 
of JavaScript packages. 

- Managing Dependencies:

Installing a package also installs the dependencies of the package.

- Versioning

Version of packages to install can be specified which helps to maintain versions
for dependencies. Version information is contained in *package.json* file.
Also existing packages can be updated to latest version.

- Publish

Packages, libraries can be published to *npm registry* which then can be used by
other projects. This is the way to make open-source libraries and shared in JavaScript
community.

- Scripts

Under *scripts* section in *package.json* file one can define script which executed
and used to perform tasks like running tests, building the application, or 
starting server.

```
npm install package-name
npm update
npm outdated
```
