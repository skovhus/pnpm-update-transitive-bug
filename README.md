# pnpm-update-transitive-bug

This repo demonstrates a potential bug in pnpm where transitive dependencies are unexpectatly updated when running a selective pnpm update.

Steps to reproduce:

1) `pnpm update --latest prettier` (`--latest` is not required for this to fail)
2) `git diff pnpm-lock.yaml`

```diff
diff --git a/pnpm-lock.yaml b/pnpm-lock.yaml
index 800397e..fb5563a 100644
--- a/pnpm-lock.yaml
+++ b/pnpm-lock.yaml
@@ -7,10 +7,10 @@ settings:
 dependencies:
   '@storybook/react':
     specifier: 7.0.13
-    version: 7.0.13(react-dom@17.0.2)(react@17.0.2)
+    version: 7.0.13(react-dom@18.2.0)(react@18.2.0)
   prettier:
-    specifier: 2.8.0
-    version: 2.8.0
+    specifier: 2.8.8
+    version: 2.8.8

 packages:

@@ -573,17 +573,17 @@ packages:
       util-deprecate: 1.0.2
     dev: false

-  /@storybook/react-dom-shim@7.0.13(react-dom@17.0.2)(react@17.0.2):
+  /@storybook/react-dom-shim@7.0.13(react-dom@18.2.0)(react@18.2.0):
     resolution: {integrity: sha512-7tZL42BoN2GMpuYoVmeNKLwaWBsBkww4Lva9BuJxS03qBCAqz0o3c3ETU9SCFIAzEvFMO46UErjKGyZPSDx1zw==}
     peerDependencies:
       react: ^16.8.0 || ^17.0.0 || ^18.0.0
       react-dom: ^16.8.0 || ^17.0.0 || ^18.0.0
     dependencies:
-      react: 17.0.2
-      react-dom: 17.0.2(react@17.0.2)
+      react: 18.2.0
+      react-dom: 18.2.0(react@18.2.0)
     dev: false

-  /@storybook/react@7.0.13(react-dom@17.0.2)(react@17.0.2):
+  /@storybook/react@7.0.13(react-dom@18.2.0)(react@18.2.0):
     resolution: {integrity: sha512-+D/OYCUD/r0xX6ZWXIoNLqRptBtJS8pYWevKhEip0FvB3KL7m/9+5YXgh5b539N1+k3hP7cqQuYxY/ftoJBXQw==}
     engines: {node: '>=16.0.0'}
     peerDependencies:
@@ -599,7 +599,7 @@ packages:
       '@storybook/docs-tools': 7.0.13
       '@storybook/global': 5.0.0
       '@storybook/preview-api': 7.0.13
-      '@storybook/react-dom-shim': 7.0.13(react-dom@17.0.2)(react@17.0.2)
+      '@storybook/react-dom-shim': 7.0.13(react-dom@18.2.0)(react@18.2.0)
       '@storybook/types': 7.0.13
       '@types/escodegen': 0.0.6
       '@types/estree': 0.0.51
@@ -611,9 +611,9 @@ packages:
       html-tags: 3.3.1
       lodash: 4.17.21
       prop-types: 15.8.1
-      react: 17.0.2
-      react-dom: 17.0.2(react@17.0.2)
-      react-element-to-jsx-string: 15.0.0(react-dom@17.0.2)(react@17.0.2)
+      react: 18.2.0
+      react-dom: 18.2.0(react@18.2.0)
+      react-element-to-jsx-string: 15.0.0(react-dom@18.2.0)(react@18.2.0)
       ts-dedent: 2.2.0
       type-fest: 2.19.0
       util-deprecate: 1.0.2
@@ -1363,8 +1363,8 @@ packages:
     engines: {node: '>= 0.8.0'}
     dev: false

-  /prettier@2.8.0:
-    resolution: {integrity: sha512-9Lmg8hTFZKG0Asr/kW9Bp8tJjRVluO8EJQVfY2T7FMw9T5jy4I/Uvx0Rca/XWf50QQ1/SS48+6IJWnrb+2yemA==}
+  /prettier@2.8.8:
+    resolution: {integrity: sha512-tdN8qQGvNjw4CHbY+XXk0JgCXn9QiF21a55rBe5LJAU+kDyC4WQn4+awm2Xfk2lQMk5fKup9XgzTZtGkjBdP9Q==}
     engines: {node: '>=10.13.0'}
     hasBin: true
     dev: false
@@ -1393,18 +1393,17 @@ packages:
     resolution: {integrity: sha512-BBea6L67bYLtdbOqfp8f58fPMqEwx0doL+pAi8TZyp2YWz8R9G8z9x75CZI8W+ftqhFHCpEX2cRnUUXK130iKA==}
     dev: false

-  /react-dom@17.0.2(react@17.0.2):
-    resolution: {integrity: sha512-s4h96KtLDUQlsENhMn1ar8t2bEa+q/YAtj8pPPdIjPDGBDIVNsrD9aXNWqspUe6AzKCIG0C1HZZLqLV7qpOBGA==}
+  /react-dom@18.2.0(react@18.2.0):
+    resolution: {integrity: sha512-6IMTriUmvsjHUjNtEDudZfuDQUoWXVxKHhlEGSk81n4YFS+r/Kl99wXiwlVXtPBtJenozv2P+hxDsw9eA7Xo6g==}
     peerDependencies:
-      react: 17.0.2
+      react: ^18.2.0
     dependencies:
       loose-envify: 1.4.0
-      object-assign: 4.1.1
-      react: 17.0.2
-      scheduler: 0.20.2
+      react: 18.2.0
+      scheduler: 0.23.0
     dev: false

-  /react-element-to-jsx-string@15.0.0(react-dom@17.0.2)(react@17.0.2):
+  /react-element-to-jsx-string@15.0.0(react-dom@18.2.0)(react@18.2.0):
     resolution: {integrity: sha512-UDg4lXB6BzlobN60P8fHWVPX3Kyw8ORrTeBtClmIlGdkOOE+GYQSFvmEU5iLLpwp/6v42DINwNcwOhOLfQ//FQ==}
     peerDependencies:
       react: ^0.14.8 || ^15.0.1 || ^16.0.0 || ^17.0.1 || ^18.0.0
@@ -1412,8 +1411,8 @@ packages:
     dependencies:
       '@base2/pretty-print-object': 1.0.1
       is-plain-object: 5.0.0
-      react: 17.0.2
-      react-dom: 17.0.2(react@17.0.2)
+      react: 18.2.0
+      react-dom: 18.2.0(react@18.2.0)
       react-is: 18.1.0
     dev: false

@@ -1425,12 +1424,11 @@ packages:
     resolution: {integrity: sha512-Fl7FuabXsJnV5Q1qIOQwx/sagGF18kogb4gpfcG4gjLBWO0WDiiz1ko/ExayuxE7InyQkBLkxRFG5oxY6Uu3Kg==}
     dev: false

-  /react@17.0.2:
-    resolution: {integrity: sha512-gnhPt75i/dq/z3/6q/0asP78D0u592D5L1pd7M8P+dck6Fu/jJeL6iVVK23fptSUZj8Vjf++7wXA8UNclGQcbA==}
+  /react@18.2.0:
+    resolution: {integrity: sha512-/3IjMdb2L9QbBdWiW5e3P2/npwMBaU9mHCSCUzNln0ZCYbcfTsGbTJrU/kGemdH2IWmB2ioZ+zkxtmq6g09fGQ==}
     engines: {node: '>=0.10.0'}
     dependencies:
       loose-envify: 1.4.0
-      object-assign: 4.1.1
     dev: false

   /readable-stream@3.6.2:
@@ -1451,11 +1449,10 @@ packages:
     resolution: {integrity: sha512-rp3So07KcdmmKbGvgaNxQSJr7bGVSVk5S9Eq1F+ppbRo70+YeaDxkw5Dd8NPN+GD6bjnYm2VuPuCXmpuYvmCXQ==}
     dev: false

-  /scheduler@0.20.2:
-    resolution: {integrity: sha512-2eWfGgAqqWFGqtdMmcL5zCMK1U8KlXv8SQFGglL3CEtd0aDVDWgeF/YoCmvln55m5zSk3J/20hTaSBeSObsQDQ==}
+  /scheduler@0.23.0:
+    resolution: {integrity: sha512-CtuThmgHNg7zIZWAXi3AsyIzA3n4xx7aNyjwC2VJldO2LMVDhFK+63xGqq6CsJH4rTAt6/M+N4GhZiDYPx9eUw==}
     dependencies:
       loose-envify: 1.4.0
-      object-assign: 4.1.1
     dev: false

   /semver@6.3.0:
```
