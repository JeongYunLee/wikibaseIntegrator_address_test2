# WikibaseIntegrator


### ๐ local wikibase์ ๋ฐ์ดํฐ import ํ์คํธ ๊ฒฐ๊ณผ

[์ฐธ๊ณ ์๋ฃ]
- ๊นํ: https://github.com/SemanticLab/data-2-wikibase
- ๊ฐ์ด๋: https://medium.com/@thisismattmiller/wikibase-for-research-infrastructure-part-1-d3f640dfad34

### ๐ import ๋ฐ์ดํฐ ๊ตฌ์กฐ
- __properties__: importํ  ๋ฐ์ดํฐ์ ์ปฌ๋ผ(wikidata์์๋ statements ๋ถ๋ถ). type๊ณผ description์ ๋ฏธ๋ฆฌ ์ง์ ํด์ค์ผ ํจ. ๊ฐ๊ฐ์ ํ์ด์ง๋ฅผ ์์ฑํ๊ณ  PID๋ฅผ ๋ถ์ฌํจ
- __core items__: ํต์ ์ดํ ๊ฐ์ ๋๋. ๊ฐ๊ฐ์ ํ์ด์ง๋ฅผ ์์ฑํ๊ณ  QID๋ฅผ ๋ถ์ฌํจ
- __items__: importํ  ๋ฐ์ดํฐ. ์ปฌ๋ผ๋ช์ properties์์ ๋ถ์ฌํ PID์ datatype์ `PID:datatype`๊ณผ ๊ฐ์ ํํ๋ก ์์ ํด์ค์ผ ํจ. ๊ฐ item์ ์๋จ์ ์๊ธฐ๋ ๋ฐ์ค (language, label, description ๋ฑ ๋ณด์ฌ์ฃผ๋)์ ๋ฃ์ ๋ด์ฉ์ `PID:datatype`์ ๊ฐ์ ํํ๊ฐ ์๋ ์ผ๋ฐ ๋ณ์๊ฐ(์์ ์ง์  ๊ฐ๋ฅ)์ผ๋ก ์ ์งํจ. ๊ฐ๊ฐ์ ํ์ด์ง๋ฅผ ์์ฑํ๊ณ  PID๋ฅผ ๋ถ์ฌํจ


# 1.  ๊ฐ์ํ๊ฒฝ ์ค์ 

> ๐ก ๊ฐ์ํ๊ฒฝ์์ ์ค์นํด์ผ ํ๋ ์ด์ .    
> - pywikibot์ `pip isntall pywikibot` ํ์ ๋๋ local์ wikibase์ ์ฐ๊ฒฐํ๊ธฐ ์ํด์ ํฌํธ ๋ฒํธ ๋ณ๊ฒฝํ๋ ํ์ผ์ ์์ ํด์ค ์ ์์. 
> - pywikibot ๊นํ์ ํด๋ก ํด์ (ํ์ผ์ด๋ฆ core) ํ์ ํ์ผ๋ค ์์ ํ๊ณ (์๋ ์ฐธ๊ณ ) ๊ฐ์ํ๊ฒฝ์์ ๋ถ๋ฌ์์ ๋ชจ๋ ์ํฌํธํด์ ํด๊ฒฐ
> - ๊ธฐ๋ณธ ๊ฐ์ํ๊ฒฝ(?) ๋ง๋ค์ด์ ํด๋ ๋๋๋ฐ, ์ฐ๊ฒฐ์ด ์ ์๋ผ์ ์๋์ฝ๋ค์์ ๊ฐ์ํ๊ฒฝ ๋ง๋  ๊ฒ (๋ก์ปฌ python kernel ์ฐ๊ฒฐ์ด ๋ญ๊ฐ ๊ผฌ์ธ๋ฏ. ๊ทธ๋ฅ ๊ฐ์ํ๊ฒฝ ๋ง๋ค์ด์ ์ฐ๊ฒฐ ์ ๋๋ฉด ์๋์ฝ๋ค์์ ์๋ง๋ค์ด๋ ๋จ)


### 1.1. [์๋์ฝ๋ค ๊ฐ์ํ๊ฒฝ ์ค์ ](https://sdc-james.gitbook.io/onebook/2./2.1./2.1.1./2-conda-virtual-environments)

- `conda create -n wikibase python=3.7`
- ๊ฐ์ํ๊ฒฝ ์คํํ๊ธฐ `conda activate wikibase`
    
    terminal์ด๋ jupyter notebook kernel์ด๋ ๋๋ค ๊ฐ์ํ๊ฒฝ์ผ๋ก ์ค์ ๋๋์ง ํ์ธํ๊ธฐ
    

# 2. github repo๋ง๋ค์ด์ clone

- cloneํ ํด๋์ ipynb ํ์ผ ํ๋ ๋ง๋ค๊ณ  ๊ฐ์ํ๊ฒฝ kerneldmfh ์ ์ํ๊ธฐ

# 3. pywikibot ์ค์นํ๊ธฐ

### 3.1. pywikibot git clone

- ํด๋น ๊นํ ๊ฐ์ด๋ ์ฐธ๊ณ : โฃ
- `git clone https://gerrit.wikimedia.org/r/pywikibot/core.git`

### 3.2. ์ถ๊ฐ ์ค์นํ๊ธฐ

1. `pip install requests`
2. `pip install -r requirements.txt`
3. cd core ๋ค์ด๊ฐ์ `git submodule update --init`  โ ์กฐ๊ธ ์ค๋๊ฑธ๋ฆผ
4. `python pwb.py login -all` 
    
    ์ด๊ฑฐ ํ๋ฉด `NOTE: [user-config.py](http://user-config.py/) was not found!` ์ด๋ผ๋ ๋ง ๋์ค๋ฉด์ ์๋ก ์์ฑ ์์l
    
    ![Untitled](/README_images/Untitled.png)
    
    - family ์ ํํ  ๋ mediawiki๋ก ์งํ (wikidata๋ ๋๊ธด ํ๋๋ฐ ์ธ์ด ์ค์  ๋ถ๋ถ์ด ํ์คํ์ง ์์)
    - username, bot name, bot password ์น๊ณ  ๋์ ์๋์ ๊ฐ์ ์ง๋ฌธ ๋์์ ๋ ๋ค a(์ ์ฒด ๋ค ์ ํํจ) ๋๋ฅด๋ฉด [user-config.py](http://user-config.py) ํ์ผ ์์ฑ ์๋ฃ๋จ
    
    ![Untitled](/README_images/Untitled%201.png)
    

### 3.3. core/user-config.py ํ์ผ ์์ ํ๊ธฐ

- [user-config.py](http://user-config.py) ํ์ผ ์ ์์ฑ๋์๋์ง ํ์ธํ๊ธฐ
- ์ถ๊ฐ์์ ํ๊ธฐ
    - `family_files['wikipedia'] = '[http://localhost:4100/](http://localhost:4100/)'` ์ถ๊ฐ
    - paddword_file ๊ฒฝ๋ก ์ง์ 
    - mylang ์ ๋ค๋ฅธ ์ธ์ด๋ ๋ฃ์ด์ฃผ๊ณ  ์ถ๋ค๋ฉด ๋๊ฐ์ ํ์์ผ๋ก ๋ฃ์ผ๋ฉด ๋จ (ex. `mylnag = 'ko'`)
    
    ![Untitled](/README_images/Untitled%202.png)
    

### 3.4. core/user-password.py ํ์ผ ์์ ํ๊ธฐ

- ํ์์ด ์๋์ ๋ค๋ฅด๊ฒ ์ ์ฅ๋์ด ์์ ์ ์์. ์๋์ ๊ฐ์ ํ์์ผ๋ก ์์ ํ๊ธฐ
    
    ![Untitled](/README_images/Untitled%203.png)
    

### 3.5. core/pywikibot/config.py ํ์ผ ์์ ํ๊ธฐ

- user_config_file ๋ณ์์ get_user_confifg_file() ํจ์ ์ฐ์ง ๋ง๊ณ  ๊ทธ๋ฅ [user-config.py](http://user-config.py) ๊ฒฝ๋ก๋ก ๋ฐ๋ก ๋ฃ์ด์ฃผ๊ธฐ
    
    ![Untitled](/README_images/Untitled%204.png)
    

# 4. ipynb: CONNECT

1. core์ ๊ฒฝ๋ก๋ฅผ sys.path์ ์ถ๊ฐ
    
    ```python
    import sys
    sys.path.append('/Users/jeongyunl/Documents/GitHub/wikibaseIntegrator_jyl/core')
    print(sys.path)
    ```
    
2. local wikibase ์ฐ๊ฒฐํ๊ธฐ
    
    ```python
    from wikibaseintegrator import WikibaseIntegrator
    from wikibaseintegrator.wbi_config import config as wbi_config
    
    wbi_config['MEDIAWIKI_API_URL'] = 'http://localhost:4100/w/api.php'
    wbi_config['SPARQL_ENDPOINT_URL'] = 'http://localhost:8834/proxy/wdqs/bigdata/namespace/wdq/sparql'
    wbi_config['WIKIBASE_URL'] = 'http://wikibase.svc'
    wbi_config['USER_AGENT'] = 'MyWikibaseBot/1.0 (https://www.wikidata.org/wiki/User:JeongYun Lee)'
    ```
    
3. login
    
    ```python
    from wikibaseintegrator import wbi_login
    
    login_instance = wbi_login.Login(user='JeongYun Lee', password='*****, mediawiki_api_url='http://localhost:4100/w/api.php')
    ```
    
4. pywikibot install
    
    ```python
    import pywikibot, json, csv, sys
    from pywikibot import family
    ```
    

# 5. ipynb: ADD PROPERTIES

```python

"""
    Notes:
    We need to remove the built in throttling because we 
    are working on our own localhost running wikibase, we don't
    care if we do a ton of requests, we are likely the only user
"""
# over write it
def wait(self, seconds):
    """Wait for seconds seconds.
    Announce the delay if it exceeds a preset limit.
    """
    pass

pywikibot.throttle.Throttle.wait = wait

if __name__ == "__main__":

    csv_path = '/Users/jeongyunl/Documents/GitHub/wikibaseIntegrator_address_test2/testData/add_properties.csv'
    csv_file = open(csv_path,'r', encoding='utf-8-sig')
    csv_reader = csv.DictReader(csv_file)

	  ### ๋ก๊ทธ์ธ ์ด๋ฏธ ํ์ผ๋ฏ๋ก ์ํด๋ ๋จ
    site = pywikibot.Site('mediawiki:mediawiki')
    #site.login()

    complete_data = []

    for row in csv_reader:
        row = dict(row)
        
        data = {
            'datatype': row['Datatype'],  # mandatory
            'descriptions': {
                'ko': {
                    'language': 'ko',
                    'value': row['Property Description']
                }
            },
            'labels': {
                'ko': {
                    'language': 'ko',
                    'value': row['Property Label']
                }
            }
        }

        params = {
            'action': 'wbeditentity',
            'new': 'property',
            'data': json.dumps(data),
            'summary': 'bot adding in properties',
            'token': site.tokens['csrf']
            # 'token': site.tokens['edit']
        }

        req = site._simple_request(**params)
        results = req.submit()

        row['PID'] = results['entity']['id']

        print(row['PID'], row['Property Label'])
        complete_data.append(row)

    csv_file.close()

    with open(csv_path+'_updated.csv','w') as out:

        fieldnames = list(complete_data[0].keys())
        writer = csv.DictWriter(out, fieldnames=fieldnames)

        writer.writeheader()
        writer.writerows(complete_data)
```

# 6. ipynb: ADD CORE ITEMS

```python
import wikidataintegrator as WI
import requests, csv, sys, re

########## part1 ##########
WI.wdi_core.WDItemEngine.core_props = { 
    'P50': {
        'datatype': 'string',
        'name': '์๋ณ์', 
        'domain': ['addresTerms'], # this is a wikidataintergrator thing, to group properties together
        'core_id': True 
    }
}

use_unique_property = 'P50:string'

if __name__ == "__main__":

    csv_path = '/Users/jeongyunl/Documents/Github/wikibaseintegrator_address_test2/testData/add_core_items.csv'
    csv_file = open(csv_path,'r', encoding='utf-8-sig')
    csv_reader = csv.DictReader(csv_file)

    complete_data = []
    errors_data = []

    for row in csv_reader:
        row = dict(row)

        data = []

        # properties stuff     
        for key in row:

            # is it a property field
            if key.find(':') > -1 and key[0] == "P":
                PID, data_type = key.split(':')

                # there are few other data types need to add...
                try:
                    if data_type.lower() == 'string':
                        if row[key] is not None and row[key].strip() != '':
                            statement = WI.wdi_core.WDString(value=row[key], prop_nr=PID)
                            data.append(statement)
                    elif data_type.lower() == 'url':
                        if row[key] is not None and row[key].strip() != '':
                            statement = WI.wdi_core.WDUrl(value=row[key], prop_nr=PID)
                            data.append(statement)
                    elif data_type.lower() == 'wikibase-item':
                        if row[key] is not None and row[key].strip() != '':
                            statement = WI.wdi_core.WDItemID(value=row[key], prop_nr=PID)
                            data.append(statement)

                    
                except Exception as e:
                    print("There was an error with this part1, skipping:")
                    print(row)
                    print(e)
                    errors_data.append(row)
                    data = "error"

        if data == 'error':
            continue

        if use_unique_property in row:
            item_name = row[use_unique_property]
        else:
            item_name = None

########## part2 ##########
        domain = 'addresTerms'

        try:
            wd_item = WI.wdi_core.WDItemEngine(new_item=True, data=data, mediawiki_api_url="http://localhost:4100/w/api.php")

            # set the label and description if exists
            if 'Label' in row:
                if row['Label'] is not None and row['Label'].strip() != '':
                    wd_item.set_label(row['Label'])

            if 'Description' in row:
                if row['Description'] is not None and row['Description'].strip() != '':
                    wd_item.set_description(row['Description'])
       

            # write
            r = wd_item.write(login_instance)
            print("goodbye!")
            
            # QID is returned
            row['QID'] = r

            print(row['QID'], row['Label'])

            
            complete_data.append(row)

        except Exception as e:
            print("There was an error with this part2, skipping:")
            print(row)
            print(e)
            errors_data.append(row)
            data = "error"

    csv_file.close()

    with open(csv_path+'_updated.csv','w') as out:

        fieldnames = list(complete_data[0].keys())
        writer = csv.DictWriter(out, fieldnames=fieldnames)

        writer.writeheader()
        writer.writerows(complete_data)

    if len(errors_data) > 0:
        with open(csv_path+'_errors.csv','w') as out:

            fieldnames = list(errors_data[0].keys())
            writer = csv.DictWriter(out, fieldnames=fieldnames)

            writer.writeheader()
            writer.writerows(errors_data)
```

# 7. ipynb: ADD ITEMS

ADD CORE ITEMS์ ์ฝ๋ ๋์ผํจ

```python
import wikidataintegrator as WI
import requests, csv, sys, re

########## part1 ##########
WI.wdi_core.WDItemEngine.core_props = { 
    'P50': {
        'datatype': 'string',
        'name': '์๋ณ์', 
        'domain': ['addresTerms'], # this is a wikidataintergrator thing, to group properties together
        'core_id': True 
    }
}

use_unique_property = 'P8:string'

if __name__ == "__main__":

    csv_path = '/Users/jeongyunl/Documents/Github/wikibaseintegrator_address_test2/testData/add_core_items.csv'
    csv_file = open(csv_path,'r', encoding='utf-8-sig')
    csv_reader = csv.DictReader(csv_file)

    complete_data = []
    errors_data = []

    for row in csv_reader:
        row = dict(row)

        data = []

        # properties stuff     
        for key in row:

            # is it a property field
            if key.find(':') > -1 and key[0] == "P":
                PID, data_type = key.split(':')

                # there are few other data types need to add...
                try:
                    if data_type.lower() == 'string':
                        if row[key] is not None and row[key].strip() != '':
                            statement = WI.wdi_core.WDString(value=row[key], prop_nr=PID)
                            data.append(statement)
                    elif data_type.lower() == 'url':
                        if row[key] is not None and row[key].strip() != '':
                            statement = WI.wdi_core.WDUrl(value=row[key], prop_nr=PID)
                            data.append(statement)
                    elif data_type.lower() == 'wikibase-item':
                        if row[key] is not None and row[key].strip() != '':
                            statement = WI.wdi_core.WDItemID(value=row[key], prop_nr=PID)
                            data.append(statement)

                    
                except Exception as e:
                    print("There was an error with this part1, skipping:")
                    print(row)
                    print(e)
                    errors_data.append(row)
                    data = "error"

        if data == 'error':
            continue

        if use_unique_property in row:
            item_name = row[use_unique_property]
        else:
            item_name = None

########## part2 ##########
        domain = 'addresTerms'

        try:
            wd_item = WI.wdi_core.WDItemEngine(new_item=True, data=data, mediawiki_api_url="http://localhost:4100/w/api.php")

            # set the label and description if exists
            if 'Label' in row:
                if row['Label'] is not None and row['Label'].strip() != '':
                    wd_item.set_label(row['Label'])

            if 'Description' in row:
                if row['Description'] is not None and row['Description'].strip() != '':
                    wd_item.set_description(row['Description'])
       

            # write
            r = wd_item.write(login_instance)
            print("goodbye!")
            
            # QID is returned
            row['QID'] = r

            print(row['QID'], row['Label'])

            
            complete_data.append(row)

        except Exception as e:
            print("There was an error with this part2, skipping:")
            print(row)
            print(e)
            errors_data.append(row)
            data = "error"

    csv_file.close()

    with open(csv_path+'_updated.csv','w') as out:

        fieldnames = list(complete_data[0].keys())
        writer = csv.DictWriter(out, fieldnames=fieldnames)

        writer.writeheader()
        writer.writerows(complete_data)

    if len(errors_data) > 0:
        with open(csv_path+'_errors.csv','w') as out:

            fieldnames = list(errors_data[0].keys())
            writer = csv.DictWriter(out, fieldnames=fieldnames)

            writer.writeheader()
            writer.writerows(errors_data)
```
