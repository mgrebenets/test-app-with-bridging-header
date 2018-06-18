
def system_framework(name):
    return '$SDKROOT/System/Library/Frameworks/%s.framework' % name


def developer_framework(name):
    return '$PLATFORM_DIR/Developer/Library/Frameworks/%s.framework' % name

def dependency(name):
    return ':' + name

def sample_app_binary(
    name,
    **kwargs
):
    binary_name = name + 'Binary'
    apple_binary(
        name=binary_name,
        module_name=name,
        modular=True,
        visibility=['PUBLIC'],
        entitlements_file='Sources/Entitlements.entitlements',
        preprocessor_flags=[
            '-fobjc-arc',
            '-Wno-objc-designated-initializers',
        ],
        headers=glob([
            'Sources/**/*.h',
        ]),
        exported_headers=glob([
            'Sources/**/*.h',
        ]),
        srcs=glob([
            'Sources/**/*.swift',
            'Sources/**/*.m'
        ]),
        bridging_header='Sources/Bridging-Header.h',
        frameworks=[
            system_framework('Foundation'),
            system_framework('UIKit'),
        ],
        **kwargs
    )
    return dependency(binary_name)


def sample_app_bundle(
    name,
    **kwargs
):
    apple_bundle(
        name=name,
        visibility=['PUBLIC'],
        binary=sample_app_binary(name=name),
        extension='app',
        info_plist='Sources/Info.plist',
        **kwargs
    )


sample_app_bundle(
    name='SampleApp',
    tests=[dependency('SampleAppTests')]
)

apple_test(
    name='SampleAppTests',
    info_plist='Tests/Info.plist',
    info_plist_substitutions={
        'PRODUCT_BUNDLE_IDENTIFIER': 'org.' + 'SampleAppTests',
    },
    srcs=glob([
        'Tests/**/*.swift',
        'Tests/**/*.m',
    ]),
    # test_host_app=dependency('SampleApp'),
    deps=[
        dependency('SampleApp'),
    ],
    frameworks=[
        developer_framework('XCTest'),
    ]
)