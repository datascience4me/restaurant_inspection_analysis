 - `api_access_keys`: oauth keys for accessing the yelp api.
 - `search.py`: Command line interface to the Yelp Search API. `python search.py --help`

This script requires the oauth2 library which you can install via:

	sudo easy_install oauth2

Search for `bars` in `sf`:

	python search.py --consumer_key="CONSUMER_KEY" --consumer_secret="CONSUMER_SECRET" \
	--token="TOKEN" --token_secret="TOKEN_SECRET" --location="sf" --term="bars"

- `get_nabe_restaurants.sh`: shell script that uses search.py for restaurants in user-specified chicago neighborhoods
- `get_chi_restaurants.sh`: gets all restaurants in chicago, 20 at time. dead end because yelp doesn't let you use offsets > 1000 in search api queries
- `get_nabe_totals.sh`: gets 20 restaurants for each yelp-defined chicago neighborhood. the idea is to use the 'total' values in the api response to build a list of neighborhoods and the restaurants in them to see if it's viable to implement chicago-wide script for each neighborhood.
- `nabe_totals.json`: json response for above script
- `nabe_totals.txt`: sortable text file of nabe total results. generate from .json through pythpn interpreter. due to duplicate restaurant results, around a third of the 110 yelp neighborhoods have over 1000 restaurants, so nabe-by-nabe approach to getting data isn't viable.

- `yelp_api.py` - Class that encapsulates yelp search api so that it can be used without cli. Currently broken.
