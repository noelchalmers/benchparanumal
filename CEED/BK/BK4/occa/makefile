
PROJ_DIR=./
CORE_DIR=../../../core

ifndef OCCA_DIR
ERROR:
	@echo "ERROR:  Environment variable OCCA_DIR is not set."
endif

include ${OCCA_DIR}/scripts/Makefile

compiler = mpic++
compilerFlags += -Ddfloat=double
compilerFlags += -Ddlong=int
compilerFlags += -DdfloatString='"double"'
compilerFlags += -DdlongString='"int"'

${PROJ_DIR}/BK4: ${PROJ_DIR}/BK4.cpp  ${CORE_DIR}/meshBasis.cpp
	$(compiler) -DOCCA_VERSION_1_0 $(compilerFlags) -o BK4 $(linkerFlags) ${PROJ_DIR}/BK4.cpp -I${CORE_DIR}/ ${CORE_DIR}/meshBasis.cpp $(paths) -L${OCCA_DIR}/lib $(flags) -locca -llapack -lblas
#$(linkerFlags)


$(oPath)/%.o:$(sPath)/%.cpp $(wildcard $(subst $(sPath)/,$(iPath)/,$(<:.cpp=.hpp))) $(wildcard $(subst $(sPath)/,$(iPath)/,$(<:.cpp=.tpp)))
	$(compiler) -DOCCA_VERSION_1_0 $(compilerFlags) -o $@ $(flags) -c $(paths) $<

clean:
	rm -f ${PROJ_DIR}/BK4

