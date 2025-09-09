# 📦 NPM CHEAT SHEET

### 🚀 START A PROJECT

- `npm init` - _create package.json_
- `npm init -y` - _create with default_

### 📥 INSTALL PACKAGES

- `npm install <pkg>` - install locally
- `npm install -g <pkg>` - install globally
- `npm install <pkg>@version` - install specific version
- `npm install` or `npm i` - install all from package.json

### 🔧 SAVE DEPENDENCIES

- `npm install <pkg> --save` - save to dependencies (default)
- `npm install <pkg> --save-dev` - save to dev dependencies

### 🧹 UNINSTALL

- `npm uninstall <pkg>` - remove local package
- `npm uninstall -g <pkg>` - remove global package

### 🔁 UPDATE

- `npm update` - update all packages
- `npm update <pkg>` - update specified package
- `npm prune` - remove unused packages
- `npm cache clean --force` - clear npm cache

### 📂 INFO & CHECKS

- `npm list` - show installed packages
- `npm list -g` - show globally installed packages
- `npm outdated` - show outdated packages
- `npm info <pkg>` - get package details

### 🧪 RUN SCRIPTS

- `npm run <script>` - run script from package.json
- `npm test` - run test script

### 🔨 SAMPLE `package.json` SCRIPTS

```json
"scripts":{
  "start" : "node index.js",
  "dev" : "nodemon app.js",
  "build" : "vite build",
}
```

### 🔍SEARCH & CONFIG

- `npm search <pkg>` - search npm registry
- `npm help` - show help docs
- `npm config set <key>` or `npm config get <key>` - set or get config values

### SEMVER SYMBOLS MEANING

- `^1.2.3` - accept updates that does'nt change the first number (Major) -(1.x.x)
- `~1.2.3` - accept only patch updates-(1.2.x)
- `1.2.3` - exact version only
- `*` - any version
- `>=1.2.3` - minimum version
- `<=1.2.3` - maximum version
