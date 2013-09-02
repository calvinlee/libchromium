# When adding a new dependency, please update the top-level .gitignore file
# # to list the dependency's destination directory.

vars = {
  "github": "http://github.com/%s/%s.git",
  "googlecode_url": "http://%s.googlecode.com/svn",
  "chromium_git": "https://chromium.googlesource.com/",

  "chromium_svn": "http://src.chromium.org/svn/trunk",

  # http://src.chromium.org/svn/releases/31.0.1604.0/
  "chromium_revision": "218165",

  "gtm_revision": "625",
}

deps = {
  # Main source tree.
  "chromium/src/":
    Var("chromium_svn") + "/src@" + Var("chromium_revision"),

  # depot_tools, include gyp, ninja etc.
  "chromium/tools/depot_tools":
    Var("chromium_svn") + "/tools/depot_tools@" + Var("chromium_revision"),

  # Base depends on it?
  "chromium/src/third_party/icu":
    Var("chromium_svn") + "/deps/third_party/icu46@219032",

  # chromium/src/testing dependencies.
  "chromium/src/testing/gtest":
    (Var("googlecode_url") % "googletest") + "/trunk@629",
  "chromium/src/testing/gmock":
    (Var("googlecode_url") % "googlemock") + "/trunk@410",

  "chromium/src/tools/grit":
    (Var("googlecode_url") % "grit-i18n") + "/trunk@129",

  # chromium/src/build dependencies. gyp_chromium.
  "chromium/src/tools/gyp":
    (Var("googlecode_url") % "gyp") + "/trunk@1707",

  # We no not use iossim
  "chromium/src/testing/iossim":
    None,
}

hooks = [
  {
    # configure overrides.
    "pattern": ".",
    "action": ["python", "libchromium/setup.py"],
  },
  {
    "pattern": ".",
    "action": ["python",
               "chromium/src/build/gyp_chromium",
               "demo/demo.gyp",
               "--depth=chromium/src"],
  }
]
