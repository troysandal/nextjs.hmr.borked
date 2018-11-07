# nextjs.next
Illustrates how next.js HMR breaks when the project name has the suffix `.next `, as this project does.

## Steps to Reproduce
* Open a shell window and ...
```sh
mkdir ~/borked
cd ~/borked

git clone git@github.com:troysandal/nextjs.next.git
cd nextjs.next
npm i
npm run dev
# wait for server to start
```
* Open http://localhost:3000
* EXPECTED: "Welcome to next.js!" message to appear
* Open `pages/index.js`, modify the welcome message, save file.
  * EXPECTED: HMR to recompile index.js, new welcome message to appear.
  * ACTUAL: HRM doesn't kick in, same welcome message appears
* Return to shell window and...
```sh
# Ctrl-C to kill next server
cd ..
mv nextjs.next nosuffix
cd nosuffix
npm run dev
# wait for server to start
```
* Open http://locahost:3000 - you should see your modified welcome message
* Open `pages/index.js`, modify the welcome message again, save file.
  * EXPECTED: HMR to recompile index.js, new welcome message to appear.
  * ACTUAL: Works this time
