bin_PROGRAMS = foo_client foo_server

HOSTPROG=yes

foo_client_SOURCES = \
    foo_client.c \
    foo.grpc-c.c \
    foo.grpc-c.h

foo_server_SOURCES = \
    foo_server.c \
    foo.grpc-c.c \
    foo.grpc-c.h \
    foo.grpc-c.service.c

foo.grpc-c.c foo.grpc-c.h foo.grpc-c.service.c:
	protoc -I ${srcdir} --grpc-c_out=. --plugin=protoc-gen-grpc-c=../compiler/protoc-gen-grpc-c ${srcdir}/foo.proto

LDADD = \
    /usr/local/lib/libgrpc.a \
    /usr/local/lib/libgpr.a \
    /usr/local/lib/libprotobuf-c.a \
    -lpthread \
    ../lib/libgrpc-c.la

LDLIBS = 

AM_CFLAGS = \
    -I. \
    -I${srcdir}/../lib/h/ \
    -I${srcdir}/../third_party/protobuf-c \
    -I${srcdir}/../third_party/grpc/include
