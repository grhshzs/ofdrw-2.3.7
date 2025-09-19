# PDF转OFD图形界面转换工具

基于OFDRW项目开发的PDF到OFD转换图形界面工具。

## 功能特性

- **图形界面操作**: 基于Java Swing的友好用户界面
- **文件选择**: 支持通过文件选择器选择PDF文件和OFD保存位置
- **转换选项**:
  - 可选择是否复制PDF附件到OFD
  - 可选择是否复制PDF书签到OFD
- **进度显示**: 实时显示转换进度和状态
- **日志输出**: 详细的转换过程日志记录
- **异步处理**: 转换过程在后台线程执行，不阻塞界面

## 运行方式

### 方式一：使用批处理文件（推荐）

```bash
# Windows系统
run-gui.bat
```

### 方式二：手动编译运行

1. 首先确保项目已编译：
```bash
mvn compile
```

2. 编译GUI程序：
```bash
javac -cp "target/classes:ofdrw-converter/target/classes:ofdrw-core/target/classes:ofdrw-layout/target/classes:ofdrw-pkg/target/classes:ofdrw-reader/target/classes:ofdrw-font/target/classes:ofdrw-gv/target/classes:ofdrw-graphics2d/target/classes:libs/*" src/main/java/org/ofdrw/gui/PDFToOFDConverter.java
```

3. 运行GUI程序：
```bash
java -cp "src/main/java:target/classes:ofdrw-converter/target/classes:ofdrw-core/target/classes:ofdrw-layout/target/classes:ofdrw-pkg/target/classes:ofdrw-reader/target/classes:ofdrw-font/target/classes:ofdrw-gv/target/classes:ofdrw-graphics2d/target/classes:libs/*" org.ofdrw.gui.PDFToOFDConverter
```

## 使用说明

1. **选择PDF文件**: 点击"选择PDF"按钮，选择要转换的PDF文件
2. **设置保存位置**: 点击"选择位置"按钮，设置OFD文件的保存路径（系统会自动建议默认路径）
3. **配置转换选项**:
   - 勾选"复制PDF附件"将PDF中的附件一同转换到OFD中
   - 勾选"复制PDF书签"将PDF的书签结构保留到OFD中
4. **开始转换**: 点击"开始转换"按钮启动转换过程
5. **查看进度**: 观察进度条和日志区域了解转换状态
6. **完成**: 转换完成后会弹出成功提示，并显示输出文件位置

## 技术实现

- **界面框架**: Java Swing
- **PDF解析**: Apache PDFBox
- **OFD生成**: OFDRW库
- **异步处理**: SwingWorker
- **文件操作**: Java NIO

## 系统要求

- Java 8或更高版本
- Windows/Linux/macOS操作系统
- 至少512MB可用内存

## 核心代码

主要实现文件：`src/main/java/org/ofdrw/gui/PDFToOFDConverter.java`

该工具直接使用OFDRW项目中的`PDFConverter`类进行转换，确保了转换质量和兼容性。

## 注意事项

- 大文件转换可能需要较长时间，请耐心等待
- 确保有足够的磁盘空间保存转换后的OFD文件
- 转换过程中请勿关闭程序
- 如遇到转换失败，请查看日志区域的错误信息