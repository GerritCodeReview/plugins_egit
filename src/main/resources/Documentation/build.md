Build
=====

This plugin is built using Bazel.
Only the Gerrit in-tree build is supported.

Clone or link this plugin to the plugins directory of Gerrit's source
tree.

```
  git clone https://gerrit.googlesource.com/gerrit
  git clone https://gerrit.googlesource.com/plugins/@PLUGIN@
  cd gerrit/plugins
  ln -s ../../@PLUGIN@ .
```

Put the external dependency Bazel build file into the Gerrit /plugins
directory, replacing the existing empty one.

```
  cd gerrit/plugins
  rm external_plugin_deps.bzl
  ln -s @PLUGIN@/external_plugin_deps.bzl .
```

From Gerrit source tree issue the command:

```
  bazel build plugins/@PLUGIN@
```

The output is created in

```
  bazel-genfiles/plugins/@PLUGIN@/@PLUGIN@.jar
```

To execute the tests run:

```
  bazel test plugins/@PLUGIN@:@PLUGIN@_tests
```

or filtering using the comma separated tags:

````
  bazel test --test_tag_filters=@PLUGIN@ //...
````

This project can be imported into the Eclipse IDE.
Add the plugin name to the `CUSTOM_PLUGINS` set in
Gerrit core in `tools/bzl/plugins.bzl`, and execute:

```
  ./tools/eclipse/project.py
```

Note for compatibility reasons Maven build is provided, but it considered to
be deprecated and is going to be removed in one of the future versions of this
plugin.

```
  mvn clean package
```

When building with Maven, the Gerrit Plugin API must be available.
How to build the Gerrit Plugin API is described in the [Gerrit
documentation](../../../Documentation/dev-bazel.html#_extension_and_plugin_api_jar_files).
