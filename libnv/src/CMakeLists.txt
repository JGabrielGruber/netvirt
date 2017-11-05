set(CMAKE_C_FLAGS "-g -W -Wall -DHAVE_VA_COPY ${compiler_options}")

add_subdirectory(tests)

if (CMAKE_SYSTEM_NAME MATCHES "Linux")
	set(compat_src bsd-asprintf.c)
endif (CMAKE_SYSTEM_NAME MATCHES "Linux")

set(NV_SRCS
	bitv.c
	log.c
	pki.c

	${compat_src}
)

add_library(nv ${NV_SRCS})
