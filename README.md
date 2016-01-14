# Node.js Barcode Reader Addon for Linux

The sample demonstrates how to make nodejs barcode reader addon on Ubuntu with DBR (Dynamsoft Barcode Reader for Linux).

## Downloads
* [v4.0.0-pre-alpha.tar.gz][1]
* [node-v5.3.0-linux-x64.tar.gz][2]

## Install Node
1. Extract node package:

    ```
    tar -xzf node-v5.3.0-linux-x64.tar.gz
    ```

2. Open .bashrc:

    ```
    nano ~/.bashrc
    ```

3. Export node path:

    ```
    export PATH=$(YOUR_HOME)/Downloads/node-v5.3.0-linux-x64/bin:$PATH
    ```

4. Install **node-gyp**:

    ```
    npm install -g node-gyp
    ```

## Install DBR
1. Extract dbr package

    ```
    tar -xzf v4.0.0-pre-alpha.tar.gz
    ```

2. Create a symbolic link of barcode shared library:

    ```
    sudo ln -s $(DynamsoftBarcodeReader)/Redist/libDynamsoftBarcodeReaderx64.so /usr/lib/libDynamsoftBarcodeReaderx64.so
    ```

## Getting Started
1. Add DBR include and library directories to **binding.gyp**:

    ```
    {
      "targets": [
        {
          "target_name": "dbr",
          "sources": [ "dbr.cc" ],
          "include_dirs" : [
            "$(DynamsoftBarcodeReader)/Include"
          ],
          "libraries": [
            "-lDynamsoftBarcodeReaderx64", "-L$(DynamsoftBarcodeReader)/Redist"
          ]
        }
      ]
    }
    ```

2. Generate project build files:

    ```
    node-gyp configure
    ```

3. Build the project to generate **dbr.node**

    ```
    node-gyp build
    ```

4. Run **dbr.js** to test the node barcode addon.

    ```
    node dbr.js
    ```
![node barcode extension](http://www.codepool.biz/wp-content/uploads/2015/12/node_dbr_result.png)


## Online Barcode Reader with Node Addon
1. Run **server.js**:
    
    ```
    node server.js
    ```
    
2. Visit *http://localhost:2016*:
![online barcode reader with nodejs](http://www.codepool.biz/wp-content/uploads/2016/01/node-online-barcode-reader.png)


[1]:http://labs.dynamsoft.com/linux-barcode-reader-overview.htm
[2]:https://nodejs.org/en/download/

