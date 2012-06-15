# Install node on debian

Clone the repo as a normal user in your home directory.
Perhaps in `~/src/node`.

```
git clone https://github.com/joyent/node.git
```

Checkout the latest stable version
Stable versions are all even releases (0.2, 04, 0.6, 0.8)

```bash
git fetch
git tag
git checkout v0.6.13

./configure --prefix=~/local/node
make
make install
```

Symlink the directory

You need to symlink all three files node, npm, node-waf (node-waf compiles
c extensions)

# Updating node

```bash
git fetch
git checkout v0.6.19
make clean
./configure --prefix=~/local/node
make
make install
```

Don't forget to update global installed modules which are
node version dependent (like forever).

```bash
npm -g rm forever
npm -g install forever
```
