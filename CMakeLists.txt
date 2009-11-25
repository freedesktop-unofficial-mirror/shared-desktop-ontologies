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
  install(FILES ${_name} DESTINATION ${CMAKE_INSTALL_PREFIX}/share/ontology/${_group})
endmacro(INSTALL_ONTOLOGY)

# base ontologies
install_ontology(base/rdf.trig core)
install_ontology(base/rdfs.trig core)
install_ontology(base/dcterms.trig dc)
install_ontology(base/dctype.trig dc)
install_ontology(base/dces.trig dc)

# Nepomuk base ontologies
install_ontology(nrl/nrl.trig nepomuk)
install_ontology(nao/nao.trig nepomuk)

# NIE
install_ontology(nie/nie.trig nie)
install_ontology(nfo/nfo.trig nie)
install_ontology(ncal/ncal.trig nie)
install_ontology(nmo/nmo.trig nie)
install_ontology(nco/nco.trig nie)
install_ontology(nexif/nexif.trig nie)
install_ontology(nmm/nmm.trig nie)
install_ontology(nid3/nid3.trig nie)

# Nepomuk extras
install_ontology(pimo/pimo.trig pimo)
install_ontology(tmo/tmo.trig pimo)
install_ontology(nso/nso.trig nepomuk)
