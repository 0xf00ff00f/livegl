find_package(PkgConfig REQUIRED)
pkg_check_modules(FFTW3 REQUIRED IMPORTED_TARGET fftw3)
pkg_check_modules(Pulse REQUIRED IMPORTED_TARGET libpulse)
pkg_check_modules(PulseSimple REQUIRED IMPORTED_TARGET libpulse-simple)

find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(GLUT REQUIRED)
find_package(cppzmq REQUIRED)
find_package(jsoncpp REQUIRED)

add_executable(livegl shader.cpp server.cpp livegl.cpp pasink.cpp spectral.cpp)
target_link_libraries(
  livegl
  PRIVATE OpenGL::GL
          OpenGL::GLU
          GLUT::GLUT
          GLEW::GLEW
          PkgConfig::FFTW3
          cppzmq
          jsoncpp_lib
          PkgConfig::Pulse
          PkgConfig::PulseSimple)
