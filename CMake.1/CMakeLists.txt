cmake_minimum_required(VERSION 3.5.0)
project(CMake.1)

set(CMAKE_CXX_STANDARD 11)

# Definir el ejecutable
add_executable(Ejecutable main.cpp)

#Opcion para copiar menos viable 
#configure_file(${CMAKE_CURRENT_LIST_DIR}/config/config.json
        #${CMAKE_CURRENT_BINARY_DIR} COPYONLY)

# Comando personalizado para copiar el archivo después de la construcción
add_custom_command(TARGET Ejecutable POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy
    ${CMAKE_CURRENT_LIST_DIR}/config/config.json
    ${CMAKE_CURRENT_BINARY_DIR}/config.json
)

# Instalación del ejecutable en el directorio bin
install(TARGETS Ejecutable
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
)

# Instalación del archivo de configuración en el directorio bin/config
install(FILES ${CMAKE_CURRENT_LIST_DIR}/config/config.json
    DESTINATION bin/config
)

# Instalación del script launcher.sh en el directorio bin/scripts
install(PROGRAMS ${CMAKE_CURRENT_LIST_DIR}/scripts/launcher.sh
    DESTINATION bin/scripts
)