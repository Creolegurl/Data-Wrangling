import csv  
import os  
with open("masterfile.csv", 'wb') as outfile, open("data/maynycweather.csv", 'wb') as weather:  
    outWriter = csv.writer(outfile)
    outfile.write('C/A,UNIT,SCP,DATEn,TIMEn,\
    DESCn,ENTRIESn,EXITSn\n') # column names

    for name in os.listdir('./turnstile'):
    with open('./turnstile/' + name, 'rb') as infile:
        inReader = csv.reader(infile)
        for row in inReader:
            for i in xrange(3,len(row),5):
                outWriter.writerow(row[0:3] + row[i:i+5])
