#
# SPDX-FileCopyrightText: 2020 George Florea Bănuș <georgefb899@gmail.com>
#
# SPDX-License-Identifier: GPL-3.0-or-later
#

cmake_minimum_required(VERSION 3.15)

project(haruna LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(ECM 1.0.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(KDEInstallDirs)
include(ECMInstallIcons)
include(FeatureSummary)

find_package(Qt5Core)
set_package_properties(Qt5Core PROPERTIES TYPE REQUIRED)

find_package(Qt5Qml)
set_package_properties(Qt5Qml PROPERTIES TYPE REQUIRED)

find_package(Qt5Quick)
set_package_properties(Qt5Quick PROPERTIES TYPE REQUIRED)

find_package(Qt5QuickControls2)
set_package_properties(Qt5QuickControls2 PROPERTIES TYPE REQUIRED)

find_package(Libmpv)
set_package_properties(Libmpv PROPERTIES TYPE REQUIRED
    URL "https://mpv.io")

find_package(Breeze)
set_package_properties(Breeze PROPERTIES TYPE RECOMMENDED
    URL "https://api.kde.org/frameworks/breeze-icons/html/index.html")

find_package(KF5Config)
set_package_properties(KF5Config PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/kconfig/html/index.html")

find_package(KF5CoreAddons)
set_package_properties(KF5CoreAddons PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/kcoreaddons/html/index.html")

find_package(KF5FileMetaData)
set_package_properties(KF5FileMetaData PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/kfilemetadata/html/index.html")

find_package(KF5I18n)
set_package_properties(KF5I18n PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/ki18n/html/index.html")

find_package(KF5IconThemes)
set_package_properties(KF5IconThemes PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/kiconthemes/html/index.html")

find_package(KF5KIO)
set_package_properties(KF5KIO PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/kio/html/index.html")

find_package(KF5Kirigami2)
set_package_properties(KF5Kirigami2 PROPERTIES TYPE RUNTIME
    URL "https://api.kde.org/frameworks/kirigami/html/index.html")

find_package(KF5XmlGui)
set_package_properties(KF5XmlGui PROPERTIES TYPE REQUIRED
    URL "https://api.kde.org/frameworks/kxmlgui/html/index.html")

option(InstallColorSchemes "Installs breeze color schemes." OFF)

add_subdirectory(data)
add_subdirectory(src)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)
