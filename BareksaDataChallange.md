# DQLab Data Champion 3 
#### Author: Yevonnael Andrew
#### E-Mail: yevonnael.andrew@gmail.com


```python
import pymysql # untuk mengambil data dari server
import pandas as pd
```


```python
con = pymysql.connect(user='guest',
                    password = 'relational',
                    host='relational.fit.cvut.cz',
                    port=3306,
                    db='UW_std')
cur = con.cursor(pymysql.cursors.DictCursor)
```


```python
cur.execute("SHOW TABLES") #untuk melihat tabel apa saja yang tersedia dalam database
tables = [c for c in cur]
tables
```




    [{'Tables_in_UW_std': 'advisedBy'},
     {'Tables_in_UW_std': 'course'},
     {'Tables_in_UW_std': 'person'},
     {'Tables_in_UW_std': 'taughtBy'}]




```python
cur.execute('SELECT * FROM course')
course = pd.DataFrame(cur.fetchall())
course.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>course_id</th>
      <th>courseLevel</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>5</td>
      <td>Level_300</td>
    </tr>
    <tr>
      <td>1</td>
      <td>11</td>
      <td>Level_300</td>
    </tr>
    <tr>
      <td>2</td>
      <td>18</td>
      <td>Level_300</td>
    </tr>
    <tr>
      <td>3</td>
      <td>104</td>
      <td>Level_300</td>
    </tr>
    <tr>
      <td>4</td>
      <td>124</td>
      <td>Level_300</td>
    </tr>
  </tbody>
</table>
</div>




```python
course.to_csv(r'course.csv'); print("File berhasil disimpan dengan nama course.csv")
```

    File berhasil disimpan dengan nama course.csv
    


```python
cur.execute('SELECT * FROM advisedBy')
advisedBy = pd.DataFrame(cur.fetchall())
advisedBy.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>p_id</th>
      <th>p_id_dummy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>96</td>
      <td>5</td>
    </tr>
    <tr>
      <td>1</td>
      <td>118</td>
      <td>5</td>
    </tr>
    <tr>
      <td>2</td>
      <td>183</td>
      <td>5</td>
    </tr>
    <tr>
      <td>3</td>
      <td>263</td>
      <td>5</td>
    </tr>
    <tr>
      <td>4</td>
      <td>362</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
advisedBy.to_csv(r'advisedBy.csv'); print("File berhasil disimpan dengan nama advisedBy.csv")
```

    File berhasil disimpan dengan nama advisedBy.csv
    


```python
cur.execute('SELECT * FROM person')
person = pd.DataFrame(cur.fetchall())
person.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>p_id</th>
      <th>professor</th>
      <th>student</th>
      <th>hasPosition</th>
      <th>inPhase</th>
      <th>yearsInProgram</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>3</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>5</td>
      <td>1</td>
      <td>0</td>
      <td>Faculty</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>6</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>Post_Quals</td>
      <td>Year_2</td>
    </tr>
    <tr>
      <td>4</td>
      <td>7</td>
      <td>1</td>
      <td>0</td>
      <td>Faculty_adj</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
person.to_csv(r'person.csv'); print("File berhasil disimpan dengan nama person.csv")
```

    File berhasil disimpan dengan nama person.csv
    


```python
cur.execute('SELECT * FROM taughtBy')
taughtBy = pd.DataFrame(cur.fetchall())
taughtBy.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>course_id</th>
      <th>p_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0</td>
      <td>40</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1</td>
      <td>40</td>
    </tr>
    <tr>
      <td>2</td>
      <td>2</td>
      <td>180</td>
    </tr>
    <tr>
      <td>3</td>
      <td>3</td>
      <td>279</td>
    </tr>
    <tr>
      <td>4</td>
      <td>4</td>
      <td>107</td>
    </tr>
  </tbody>
</table>
</div>




```python
taughtBy.to_csv(r'taughtBy.csv'); print("File berhasil disimpan dengan nama taughtBy.csv")
```

    File berhasil disimpan dengan nama taughtBy.csv
    


```python
con.close() # Memutuskan sambungan dengan remote database
```

**Memulai proses penyatuan variabel menjadi satu file csv**

Database ini bersifat relasional, yang artinya:
1. Satu tabel (variabel) dengan tabel lainnya memiliki suatu 'key' yang identik
2. Key ini yang menjelaskan relasi dari tabel tersebut dengan tabel lainnya

<img src="https://relational.fit.cvut.cz/assets/img/datasets-generated/UW_std.svg" width="400" height="300" align="left">


Dari gambar di samping, kita bisa melihat bahwa:
1. Tabel *person*, *advisedBy* dan *taughtBy* memiliki 'key' yang sama yaitu p_id
2. Tabel taughtBy memiliki variabel course_id yang dijelaskan oleh tabel *course*

**Kita akan melakukan *FULL OUTER JOIN* untuk memastikan bahwa penggabungan data dilakukan secara utuh sehingga tidak ada data yang terbuang**

**FULL OUTER JOIN** adalah metode yang digunakan untuk menggabungkan semua baris dari dua atau lebih tabel. Dengan gabungan luar penuh, tidak ada satu baris yang dibuang.


```python
# join1: Menggabungkan tabel 'person' dengan 'advisedBy'
join1 = pd.merge(person, advisedBy, on='p_id', how='outer')

# join2: Menggabungkan tabel 'taughtBy' dengan 'course'
join2 = pd.merge(taughtBy, course, on='course_id', how ='outer')

# finaljoin: Menintegrasikan join1 dengan join2
finaljoin = pd.merge(join1, join2, on='p_id', how='outer')
```


```python
finaljoin
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>p_id</th>
      <th>professor</th>
      <th>student</th>
      <th>hasPosition</th>
      <th>inPhase</th>
      <th>yearsInProgram</th>
      <th>p_id_dummy</th>
      <th>course_id</th>
      <th>courseLevel</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>3.0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>1</td>
      <td>4.0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <td>2</td>
      <td>5.0</td>
      <td>1</td>
      <td>0</td>
      <td>Faculty</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>19.0</td>
      <td>Level_500</td>
    </tr>
    <tr>
      <td>3</td>
      <td>5.0</td>
      <td>1</td>
      <td>0</td>
      <td>Faculty</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>51.0</td>
      <td>Level_400</td>
    </tr>
    <tr>
      <td>4</td>
      <td>5.0</td>
      <td>1</td>
      <td>0</td>
      <td>Faculty</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>71.0</td>
      <td>Level_500</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>439</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>131.0</td>
      <td>Level_500</td>
    </tr>
    <tr>
      <td>440</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>135.0</td>
      <td>Level_500</td>
    </tr>
    <tr>
      <td>441</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>152.0</td>
      <td>Level_500</td>
    </tr>
    <tr>
      <td>442</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>155.0</td>
      <td>Level_500</td>
    </tr>
    <tr>
      <td>443</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>169.0</td>
      <td>Level_500</td>
    </tr>
  </tbody>
</table>
<p>444 rows × 9 columns</p>
</div>




```python
print("Hasil dari FULL JOIN dataset ini memiliki dimensi baris dan kolom: {}.".format(finaljoin.shape))

print("Ada {} nilai p_id yang unik (unique value).".format(len(finaljoin['p_id'].unique())))
```

    Hasil dari FULL JOIN dataset ini memiliki dimensi baris dan kolom: (444, 9).
    Ada 279 nilai p_id yang unik (unique value).
    


```python
finaljoin.to_csv(r'FINAL.csv'); print("File hasil olahan berhasil disimpan dengan nama FINAL.CSV")
```

    File hasil olahan berhasil disimpan dengan nama FINAL.CSV
    

#### The end of the analysis.
