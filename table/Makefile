HAPIHEAD=../data/tables/hapi.table.head.json
HAPIBODY=../data/tables/hapi.table.body.json

ALLHEAD=../data/tables/all.table.head.json
ALLBODY=../data/tables/all.table.body.json

table-ui:
	@- git clone https://github.com/rweigel/table-ui
	@- git pull https://github.com/rweigel/table-ui

serve-all:
	cd ../; make table-all
	make table-ui
	cd table-ui/ajax; python server.py 8051 $(ALLHEAD) $(ALLBODY)

serve-all-sql:
	cd ../; make table-all
	make all-sql
	python table-ui/ajax/server.py 8051 $(ALLHEAD) $(ALLBODY).sql

all-sql:
	cd ../; make table-all
	make table-ui
	make $(ALLBODY).sql

$(ALLBODY).sql: table-ui/ajax/sql/sql.py $(ALLHEAD) $(ALLBODY)
	python table-ui/ajax/sql/sql.py $(ALLHEAD) $(ALLBODY)


serve-hapi:
	cd ../; make table-hapi
	make table-ui
	python table-ui/ajax/server.py 8052 $(HAPIHEAD) $(HAPIBODY)

serve-hapi-sql:
	cd ../; make table-hapi
	make hapi-sql
	python table-ui/ajax/server.py 8052 $(HAPIHEAD) $(HAPIBODY).sql

hapi-sql:
	cd ../; make table-hapi
	make table-ui
	make $(HAPIBODY).sql

$(HAPIBODY).sql: table-ui/ajax/sql/sql.py $(HAPIHEAD) $(HAPIBODY)
	python table-ui/ajax/sql/sql.py $(HAPIHEAD) $(HAPIBODY)

