# react-qml-rust-boilerplate
A simple boilerplate to build native desktop app using react-qml and rust

![Screenshot](with-redux.png?raw=true "Redux DevTools Screenshot")

## Presequisites:
Install Qt5, yarn, rust: 
```
brew install qt
brew install yarn
curl https://sh.rustup.rs -sSf | sh
```

## Development
### Step 1. Run dev server:
```
yarn install
yarn start
```

### Step 2. Run desktop app
```
cd rust
cargo install --path .
cargo run
```

## Production Release
### Step 1. Bundle front-end codes:
```
yarn install
yarn build
```

### Step 2. Update entry URL
- Open `rust/src/main.rs`
- Edit `entry_url` to load from `qrc:/index.qml`
```
// let entry_url = QVariant::from(QString::from("http://localhost:8081/index.qml"));
// in production, use code below
let entry_url = QVariant::from(QString::from("qrc:/index.qml"));

```

### Step 3. Bundle desktop app
```
cd rust
cargo bundle --release
macdeployqt "target/release/bundle/osx/React QML Rust.app"
```