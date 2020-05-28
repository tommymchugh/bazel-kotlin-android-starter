load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

android_sdk_repository(name = "androidsdk")

RULES_JVM_EXTERNAL_TAG = "2.9"
RULES_JVM_EXTERNAL_SHA = "e5b97a31a3e8feed91636f42e19b11c49487b85e5de2f387c999ea14d77c7f45"

http_archive(
    name = "rules_jvm_external",
    sha256 = RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "com.android.support:appcompat-v7:26.1.0",
    ],
    fetch_sources = True,
    # See https://github.com/bazelbuild/rules_jvm_external/#repository-aliases
    # This can be removed if none of your external dependencies uses `maven_jar`.
    generate_compat_repositories = True,
    repositories = [
        "https://jcenter.bintray.com",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
    version_conflict_policy = "pinned",
)

load("@maven//:compat.bzl", "compat_repositories")

compat_repositories()

http_archive(
    name = "rules_android",
    sha256 = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806",
    strip_prefix = "rules_android-0.1.1",
    urls = ["https://github.com/bazelbuild/rules_android/archive/v0.1.1.zip"],
)
