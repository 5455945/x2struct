ifeq ($(GPP),)
GPP=g++
endif


INC=-I ../
ifneq ($(OS),Windows_NT)
LIBCONFIG=../thirdparty/libconfig/lib/libconfig++.a
LIBBSON=../thirdparty/libbson/lib/libbson-1.0.a -pthread -lrt
endif

json:
	$(GPP) -o $@ example_json.cpp $(INC)
	./$@
	@-rm $@

xml:
	$(GPP) -o $@ example_xml.cpp $(INC)
	./$@
	@-rm $@

libconfig:
	$(GPP) -o $@ -DXTOSTRUCT_LIBCONFIG example_libconfig.cpp $(INC) $(LIBCONFIG)
	./$@
	@-rm $@

bson:
	$(GPP) -o $@ -DXTOSTRUCT_BSON example_bson.cpp $(INC) $(LIBBSON)
	./$@
	@-rm $@

gocode:
	$(GPP) -o $@ -DXTOSTRUCT_GOCODE check.cpp $(INC) $(LIBCONFIG) $(LIBBSON)
	./$@
	@-rm $@

check:
	$(GPP) -o $@ -Wextra -Wall check.cpp $(INC) $(LIBCONFIG) $(LIBBSON)
	./$@
	@-rm $@

checkc11:
	$(GPP) -o $@ -Wextra -Wall check.cpp $(INC) $(LIBCONFIG) $(LIBBSON) -std=c++11
	./$@
	@-rm $@

nt:
	$(GPP) -o $@ check.cpp $(INC) $(LIBCONFIG) $(LIBBSON) -std=c++11 -DXNT
	./$@
	@-rm $@

expand:
	$(GPP) -E -DXTOSTRUCT_MACRO_TEST expand.cpp

os:
	echo $(OS)
