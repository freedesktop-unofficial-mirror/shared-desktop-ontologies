project(shared-desktop-ontologies)

cmake_minimum_required(VERSION 2.6)

macro(INSTALL_ONTOLOGY _name _group)
  install(FILES ${_name} DESTINATION ${CMAKE_INSTALL_PREFIX}/share/ontology/${_group})
endmacro(INSTALL_ONTOLOGY)

# base ontologies
install_ontology(base/rdf.trig base)
install_ontology(base/rdfs.trig base)
install_ontology(base/dcterms.trig base)
install_ontology(base/dctype.trig base)
install_ontology(base/dces.trig base)

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
