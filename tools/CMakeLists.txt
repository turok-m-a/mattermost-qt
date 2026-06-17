set(APP emojiMapGenerator)

add_executable(${APP}
		emojiMapGenerator.cpp
)

target_link_libraries(${APP}
        PRIVATE Qt${QT_VERSION_MAJOR}::Widgets
)
