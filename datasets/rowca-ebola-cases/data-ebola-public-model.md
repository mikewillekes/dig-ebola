## data-ebola-public-sample.csv

### PyTransforms
#### _iso_date_
From column: _Date_
>``` python
return iso8601date(getValue("Date"))
```

#### _localite_clean_
From column: _Localite_
>``` python
return clean_localite(getValue("Localite"))
```

#### _hash_
From column: _Link_
>``` python
return md5Hash(getValue("Country")+getValue("Localite")+getValue("Category")+getValue("Value")+getValue("Date")+getValue("Sources")+getValue("Link"))
```

#### _country_uri_
From column: _Country_
>``` python
return "country/"+getValue("Country").lower()
```

#### _place_uri_
From column: _hash_
>``` python
return getValue("hash")+"/place"
```

#### _source_uri_
From column: _Sources_
>``` python
return "organization/"+getValue("Sources").lower()
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _Category_ | `eb:eventType` | `eb:EbolaEvent1`|
| _Country_ | `rdfs:label` | `schema:Country1`|
| _Link_ | `rdfs:seeAlso` | `eb:EbolaEvent1`|
| _Sources_ | `rdfs:label` | `prov:Organization1`|
| _Value_ | `eb:eventValue` | `eb:EbolaEvent1`|
| _Values_ | `schema:addressLocality` | `schema:PostalAddress1`|
| _country_uri_ | `uri` | `schema:Country1`|
| _hash_ | `uri` | `eb:EbolaEvent1`|
| _iso_date_ | `schema:endDate` | `eb:EbolaEvent1`|
| _place_uri_ | `uri` | `schema:Place1`|
| _source_uri_ | `uri` | `prov:Organization1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `eb:EbolaEvent1` | `schema:location` | `schema:Place1`|
| `eb:EbolaEvent1` | `prov:hadPrimarySource` | `prov:Organization1`|
| `schema:Place1` | `schema:address` | `schema:PostalAddress1`|
| `schema:PostalAddress1` | `schema:addressCountry` | `schema:Country1`|
