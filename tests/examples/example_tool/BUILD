load("@io_bazel_rules_dotnet//dotnet:defs.bzl", "core_binary", "dotnet_binary", "net_binary")

dotnet_binary(
    name = "hello_tool",
    srcs = [
        "MyTool.cs",
    ],
    deps = [
        "//tests/examples/example_lib:MyClass",
    ],
)

core_binary(
    name = "hello_tool_core",
    srcs = [
        "MyTool.cs",
    ],
    deps = [
        "//tests/examples/example_lib:MyClass-core",
        "@io_bazel_rules_dotnet//dotnet/stdlib.core:system.console.dll",
        "@io_bazel_rules_dotnet//dotnet/stdlib.core:system.io.filesystem.dll",
        "@io_bazel_rules_dotnet//dotnet/stdlib.core:system.private.corelib.dll",
        "@io_bazel_rules_dotnet//dotnet/stdlib.core:system.runtime.dll",
        "@io_bazel_rules_dotnet//dotnet/stdlib.core:system.runtime.extensions.dll",
    ],
)

net_binary(
    name = "hello_tool_net",
    srcs = [
        "MyTool.cs",
    ],
    deps = [
        "//tests/examples/example_lib:MyClass-net",
    ],
)

genrule(
    name = "hello_single_output",
    outs = [
        "hello_world.txt",
    ],
    cmd = "$(location :hello_tool) $@",
    tools = [
        ":hello_tool",
    ],
)

genrule(
    name = "hello_multiple_outputs",
    outs = [
        "hello_world_1.txt",
        "hello_world_2.txt",
    ],
    cmd = "$(location :hello_tool) $(OUTS)",
    tools = [
        ":hello_tool",
    ],
)

genrule(
    name = "hello_single_output_core",
    outs = [
        "hello_world_core.txt",
    ],
    cmd = "$(location :hello_tool_core) $@",
    tools = [
        ":hello_tool_core",
    ],
)

genrule(
    name = "hello_multiple_outputs_core",
    outs = [
        "hello_world_1_core.txt",
        "hello_world_2_core.txt",
    ],
    cmd = "$(location :hello_tool_core) $(OUTS)",
    tools = [
        ":hello_tool_core",
    ],
)

#genrule(
#    name = "hello_single_output_net",
#    outs = [
#        "hello_world_net.txt",
#    ],
#    tools = [
#        ":hello_tool_net",
#    ],
#    cmd = "$(location :hello_tool_net) $@",
#)

#genrule(
#    name = "hello_multiple_outputs_net",
#    outs = [
#        "hello_world_1_net.txt",
#        "hello_world_2_net.txt",
#    ],
#    tools = [
#        ":hello_tool_net",
#    ],
#    cmd = "$(location :hello_tool_net) $(OUTS)",
#)
