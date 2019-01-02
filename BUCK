
apple_binary(
    name='AppBinary',
    module_name='App',
    modular=True,
    visibility=['PUBLIC'],
    entitlements_file='Sources/Entitlements.entitlements',
    preprocessor_flags=[
        '-fobjc-arc',
        '-Wno-objc-designated-initializers',
    ],
    # swift_compiler_flags=[
    #     '-import-underlying-module',
    # ],
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
    frameworks=[
        '$SDKROOT/System/Library/Frameworks/Foundation.framework',
        '$SDKROOT/System/Library/Frameworks/UIKit.framework',
    ]
)



apple_bundle(
    name='AppBundle',
    visibility=['PUBLIC'],
    binary=':AppBinary',
    extension='app',
    info_plist='Sources/Info.plist',
    tests=[':Tests']
)

apple_test(
    name='Tests',
    # modular=True,
    info_plist='Tests/Info.plist',
    info_plist_substitutions={
        'PRODUCT_BUNDLE_IDENTIFIER': 'org.' + 'Tests',
    },
    srcs=glob([
        'Tests/**/*.swift',
        'Tests/**/*.m',
    ]),
    # test_host_app=':AppBundle',
    deps=[
        ':AppBinary',
        ':AppBundle',
    ],
    frameworks=[
        '$SDKROOT/System/Library/Frameworks/Foundation.framework',
        '$SDKROOT/System/Library/Frameworks/UIKit.framework',
        '$PLATFORM_DIR/Developer/Library/Frameworks/XCTest.framework',
    ]
)