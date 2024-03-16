Resumen de mi analisis

1- Importe librerias (BeautifulSoup | requests | time | datetime)

2- Creé una variable para conectar la web (.get)

3- Obtener todo el HTML de la pagina Amazon

    soup1 = BeautifulSoup(page.content, "html.parser")

4- Que la info se vea mas prolija

    soup2 = BeautifulSoup(soup1.prettify(), "html.parser")

5- Selecciono el "titulo" y "precio" a traves de su "ID" [Uso el metodo "find" para encontrarlo y "get.text" para traerlo]

    title = soup2.find(id='productTitle').get_text()

6- Limpiar la info, sacando espacios con "strip" [Con [1:] --> quite el signo $]

    price = price.strip()[1:]
    title = title.strip()

7- Variable para almacenar el dia de hoy

    today = datetime.date.today()

8- Variable para escribir el encabezado y lo datos

    header = ['Title', 'Price', 'Date']
    data = [title, price, today]

9- Con "open" y "w" creo el CSV

    with open('AmazonWebScraperDataset.csv', 'w', newline='', encoding='UTF8') as f:
    writer = csv.writer(f)
    
    #Creo el encabezado
    writer.writerow(header)
    
    #Inserto los datos al CSV (precio y fecha)
    writer.writerow(data)
    
[[[ Se creo un EXCEL con los titulos y datos ]]]

10- Para agregar datos se coloca "a+"

    with open('AmazonWebScraperDataset.csv', 'a+', newline='', encoding='UTF8') as f:

11- Creo una funcion para poner todo

12- "while" sirve para actualizarlo cada tantos segundos
    
    while(True):
    check_price()
    [86400 segundos por 1 dia]
    time.sleep(86400)
