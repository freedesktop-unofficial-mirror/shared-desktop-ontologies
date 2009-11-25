project(shared-desktop-ontologies)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_ONTOLOGIES_VERSION_MAJOR 0)
set(CMAKE_ONTOLOGIES_VERSION_MINOR 1)
set(CMAKE_ONTOLOGIES_VERSION_STRING "${CMAKE_ONTOLOGIES_VERSION_MAJOR}.${CMAKE_ONTOLOGIES_VERSION_MINOR}")

if(NOT WIN32)
  set(PKGCONFIG_INSTALL_PREFIX "${CMAKE_INSTALL_PREFIX}/share/pkgconfig/" CACHE STRING "Base directory for pkgconfig files")
  configure_file(${CMAKE_CURRENT_SOURCE_DIR}/shared-desktop-ontologies.pc.cmake ${CMAKE_CURRENT_BINARY_DIR}/shared-desktop-ontologies.pc @ONLY)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/shared-desktop-ontologies.pc DESTINATION ${PKGCONFIG_INSTALL_PREFIX})
endif(NOT WIN32)

macro(INSTALL_ONTOLOGY _name _group)
  set(ONTO_INSTALL_DIR ${CMAKE_INSTALL_PREFIX}/share/ontology/${_group})
  configure_file("${_name}.ontology.cmake" "${CMAKE_CURRENT_BINARY_DIR}/${_name}.ontology")
  install(FILES "${CMAKE_CURRENT_BINARY_DIR}/${_name}.ontology" DESTINATION ${ONTO_INSTALL_DIR})
  install(FILES "${_name}.trig" DESTINATION ${ONTO_INSTALL_DIR})
endmacro(INSTALL_ONTOLOGY)

# base ontologies
install_ontology(base/rdf core)
install_ontology(base/rdfs core)
install_ontology(base/dcterms dc)
install_ontology(base/dctype dc)
install_ontology(base/dces dc)

# Nepomuk base ontologies
install_ontology(nrl/nrl nepomuk)
install_ontology(nao/nao nepomuk)

# NIE
install_ontology(nie/nie nie)
install_ontology(nfo/nfo nie)
install_ontology(ncal/ncal nie)
install_ontology(nmo/nmo nie)
install_ontology(nco/nco nie)
install_ontology(nexif/nexif nie)
install_ontology(nmm/nmm nie)
install_ontology(nid3/nid3 nie)

# Nepomuk extras
install_ontology(pimo/pimo pimo)
install_ontology(tmo/tmo pimo)
install_ontology(nso/nso nepomuk)
