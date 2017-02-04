load("//tools/bzl:plugin.bzl", "gerrit_plugin")

gerrit_plugin(
    name = "egit",
    srcs = glob(["src/main/java/**/*.java"]),
    resources = glob(["src/main/resources/**/*"]),
    manifest_entries = [
        "Gerrit-PluginName: egit",
        "Gerrit-Module: com.googlesource.gerrit.plugins.egit.Module",
    ],
)
