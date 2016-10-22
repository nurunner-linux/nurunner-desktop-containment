project(netrunnerdesktop)
set(PROJECT_VERSION "1.0")
set(PROJECT_VERSION_MAJOR 1)

cmake_minimum_required(VERSION 2.8.12 FATAL_ERROR)
set(QT_MIN_VERSION "5.4.0")

find_package(ECM 0.0.11 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules)

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings)
include(ECMInstallIcons)
include(ECMMarkAsTest)
include(ECMMarkNonGuiExecutable)
include(ECMOptionalAddSubdirectory)
include(FeatureSummary)
include(CheckIncludeFiles)

find_package(Qt5 ${QT_MIN_VERSION} CONFIG REQUIRED COMPONENTS
    Quick
    QuickWidgets
    DBus
    Widgets
    X11Extras
    Svg
    Concurrent
)

set(KF5_MIN_VERSION "5.12.0")
find_package(KF5 ${KF5_MIN_VERSION} REQUIRED COMPONENTS
    Auth
    Plasma
    PlasmaQuick
    DocTools
    I18n
    KCMUtils
    NewStuff
    KDELibs4Support
    Notifications
    NotifyConfig
    Attica
    Wallet
    Runner
    GlobalAccel
    Declarative
    People
    DBusAddons
)

include_directories("${CMAKE_CURRENT_BINARY_DIR}")

add_subdirectory(src)

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)