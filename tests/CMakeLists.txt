find_package(Qt5 ${QT_MIN_VERSION} REQUIRED COMPONENTS Test)

include_directories(
    ${KDEConnectCore_BINARY_DIR}
    ${CMAKE_SOURCE_DIR}
    ${CMAKE_BINARY_DIR}/plugins/sendnotifications/
)

set(kdeconnect_libraries
	kdeconnectcore
    KF5::I18n
    KF5::KIOWidgets
    Qt5::DBus
    Qt5::Network
    Qt5::Test
    qca-qt5
)

ecm_add_test(pluginloadtest.cpp LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(sendfiletest.cpp LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(networkpackettests.cpp LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(testsocketlinereader.cpp TEST_NAME testsocketlinereader LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(testsslsocketlinereader.cpp TEST_NAME testsslsocketlinereader LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(kdeconnectconfigtest.cpp TEST_NAME kdeconnectconfigtest LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(lanlinkprovidertest.cpp TEST_NAME lanlinkprovidertest LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(devicetest.cpp TEST_NAME devicetest LINK_LIBRARIES ${kdeconnect_libraries})
ecm_add_test(testnotificationlistener.cpp
             ../plugins/sendnotifications/sendnotificationsplugin.cpp
             ../plugins/sendnotifications/notificationslistener.cpp
             ../plugins/sendnotifications/notifyingapplication.cpp
             TEST_NAME testnotificationlistener
             LINK_LIBRARIES ${kdeconnect_libraries} Qt5::DBus KF5::Notifications KF5::IconThemes)
