# Make-fun
帮你更好的构建整个Pipe

## 步骤
### 克隆源码并下载子模块
* ```git clone https://github.com/pipe-fun/make-fun.git```
* ```cd make-fun ```
* ```git submodule update init```

### 创建数据库并导入表(举例)
* ```CREATE DATABASE pipe;```
* ``` cd crates/db-api```
* ```psql -d pipe -U user -f schema.sql```

### 修改配置文件
* ```mv .env.example .env```
* ```nano .env```

### 编译
* ```cd make-fun```
* ```cargo build --release```
* ```cd crates/pipe```
* ```cargo install wasm-pack```
* ```wasm-pack build --release --target web --out-name wasm --out-dir static/```

### 依次运行(使用tmux等多终端软件)
* ```cd target/release```
* ```./db-api```
* ```./pipe-core```
* ```./web-api```
* 挂载```crates/pipe/static```资源（例如Nginx）
