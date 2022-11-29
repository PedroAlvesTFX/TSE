#   How to Process TSE data LOGs

Official tools from TSE: https://www.tse.jus.br/eleicoes/eleicoes-2022/arquivos/formato-dos-arquivos-de-bu-rdv-e-assinatura-digital-17-9-22/@@download/file/formato-arquivos-bu-rdv-ass-digital.zip

Official data:https://dadosabertos.tse.jus.br/dataset/resultados-2022-boletim-de-urna
           

To read BU files you will need Python and some libraries. In directory <a href=Tools>Tools</a> you can find more instructions.

To read Log files you will need a decompress program named 7z. In Windows you can find this program in:https://www.7-zip.org/download.html
In Linux, it depends on your Linux Distribution. For example in Oracle Linux for Windows you will need install Epel repository before issue the command "yum install p7zip". On Ubuntu you just need to issue the command : 
```
apt-get install p7zip 
```
.

For BU files you will need to donwload the <a href=https://www.tse.jus.br/eleicoes/eleicoes-2022/arquivos/formato-dos-arquivos-de-bu-rdv-e-assinatura-digital-17-9-22/@@download/file/formato-arquivos-bu-rdv-ass-digital.zip>zip file in tools</a>, and install some libraries:
```
pip install asn1tools asn1crypto ed25519 ecdsa 
```

And run the following command in tools directory: 
```
python3 ./python/bu_dump.py -s spec/bu.asn1 -b bu-file.bu 
```

The result is something like this:

```
python3 ./python/bu_dump.py -a spec/bu.asn1 -b bu/o00407-4002901790057.bu
2022-11-08 08:30:52,178 - INFO - Converte bu/o00407-4002901790057.bu com as especificações ['spec/bu.asn1']
EntidadeEnvelopeGenerico:
.   cabecalho:
.   .   dataGeracao = 20221030T170530
.   .   idEleitoral = ('idPleito', 407)
.   fase = oficial
.   identificacao = ('identificacaoSecaoEleitoral', {'municipioZona': {'municipio': 40029, 'zona': 179}, 'local': 1015, 'secao': 57})
.   tipoEnvelope = envelopeBoletimUrna
EntidadeBoletimUrna:
.   cabecalho:
.   .   dataGeracao = 20221030T170530
.   .   idEleitoral = ('idPleito', 407)
.   chaveAssinaturaVotosVotavel = 2af09e8fd645d7160a3134bd6417c9187f9618281fd673c6c4eef8c98e4bdbd5
.   dadosSecaoSA = ('dadosSecao', {'dataHoraAbertura': '20221030T080001', 'dataHoraEncerramento': '20221030T170259'})
.   dataHoraEmissao = 20221030T170501
.   fase = oficial
.   identificacaoSecao:
.   .   local = 1015
.   .   municipioZona:
.   .   .   municipio = 40029
.   .   .   zona = 179
.   .   secao = 57
.   qtdEleitoresCompBiometrico = 285
.   qtdEleitoresLibCodigo = 35
.   resultadosVotacaoPorEleicao: [
.   .   .   idEleicao = 545
.   .   .   qtdEleitoresAptos = 375
.   .   .   resultadosVotacao: [
.   .   .   .   .   qtdComparecimento = 291
.   .   .   .   .   tipoCargo = majoritario
.   .   .   .   .   totaisVotosCargo: [
.   .   .   .   .   .   .   codigoCargo = ('cargoConstitucional', 'presidente')
.   .   .   .   .   .   .   ordemImpressao = 1
.   .   .   .   .   .   .   votosVotaveis: [
.   .   .   .   .   .   .   .   .   assinatura = a29fa6ebdbf9bd81e1d94e195e80cb1cb7762faae13be78718fbfe8528dfcdc6335bfda1c105e73648d1dabcfb0b5a45691977bf1634320198f908dd118c090c
.   .   .   .   .   .   .   .   .   identificacaoVotavel:
.   .   .   .   .   .   .   .   .   .   codigo = 13
.   .   .   .   .   .   .   .   .   .   partido = 13
.   .   .   .   .   .   .   .   .   quantidadeVotos = 140
.   .   .   .   .   .   .   .   .   tipoVoto = nominal
.   .   .   .   .   .   .   .   .   assinatura = 88f633b1198297b34bd939fcdaf64e706028c43e3a83d2533f08ead4daafc7396c29d413e46693157f58c123e8f4edc00d4dd0282a385a23620313fd6ac0810d
.   .   .   .   .   .   .   .   .   identificacaoVotavel:
.   .   .   .   .   .   .   .   .   .   codigo = 22
.   .   .   .   .   .   .   .   .   .   partido = 22
.   .   .   .   .   .   .   .   .   quantidadeVotos = 143
.   .   .   .   .   .   .   .   .   tipoVoto = nominal
.   .   .   .   .   .   .   .   .   assinatura = ed59112c9b55b5a738a5a558448c11dd716a3b06d889ead53b7366c9d043c75c5fa2414380765c9c1ee046e3234ee41b1460a0513bd62eb17c082babec45620c
.   .   .   .   .   .   .   .   .   quantidadeVotos = 8
.   .   .   .   .   .   .   .   .   tipoVoto = nulo
.   .   .   .   .   .   .   ] <== votosVotaveis
.   .   .   .   .   ] <== totaisVotosCargo
.   .   .   ] <== resultadosVotacao
.   ] <== resultadosVotacaoPorEleicao
.   urna:
.   .   correspondenciaResultado:
.   .   .   carga:
.   .   .   .   codigoCarga = 257282375591450377973108
.   .   .   .   dataHoraCarga = 20220925T153100
.   .   .   .   numeroInternoUrna = 1635968
.   .   .   .   numeroSerieFC = 3ba5839d
.   .   .   identificacao = ('identificacaoSecaoEleitoral', {'municipioZona': {'municipio': 40029, 'zona': 179}, 'local': 1, 'secao': 57})
.   .   numeroSerieFV = 6b76ae52
.   .   tipoArquivo = votacaoUE
.   .   tipoUrna = secao
.   .   versaoVotacao = 8.26.0.0 - Onça-pintada
```

In my experience the contents came with some dots. I don´t know if this is related to some charset conversion or not. To remove dots in archive i use the command in Linux: 
```
python3 ./python/bu_dump.py -a spec/bu.asn1 -b bu/o00407-4002901790057.bu | tr "." " "  
```

The result is more clean:
```
python3 ./python/bu_dump.py -a spec/bu.asn1 -b bu/o00407-4002901790057.bu | tr "." " "
2022-11-08 08:32:33,887 - INFO - Converte bu/o00407-4002901790057.bu com as especificações ['spec/bu.asn1']
EntidadeEnvelopeGenerico:
    cabecalho:
        dataGeracao = 20221030T170530
        idEleitoral = ('idPleito', 407)
    fase = oficial
    identificacao = ('identificacaoSecaoEleitoral', {'municipioZona': {'municipio': 40029, 'zona': 179}, 'local': 1015, 'secao': 57})
    tipoEnvelope = envelopeBoletimUrna
EntidadeBoletimUrna:
    cabecalho:
        dataGeracao = 20221030T170530
        idEleitoral = ('idPleito', 407)
    chaveAssinaturaVotosVotavel = 2af09e8fd645d7160a3134bd6417c9187f9618281fd673c6c4eef8c98e4bdbd5
    dadosSecaoSA = ('dadosSecao', {'dataHoraAbertura': '20221030T080001', 'dataHoraEncerramento': '20221030T170259'})
    dataHoraEmissao = 20221030T170501
    fase = oficial
    identificacaoSecao:
        local = 1015
        municipioZona:
            municipio = 40029
            zona = 179
        secao = 57
    qtdEleitoresCompBiometrico = 285
    qtdEleitoresLibCodigo = 35
    resultadosVotacaoPorEleicao: [
            idEleicao = 545
            qtdEleitoresAptos = 375
            resultadosVotacao: [
                    qtdComparecimento = 291
                    tipoCargo = majoritario
                    totaisVotosCargo: [
                            codigoCargo = ('cargoConstitucional', 'presidente')
                            ordemImpressao = 1
                            votosVotaveis: [
                                    assinatura = a29fa6ebdbf9bd81e1d94e195e80cb1cb7762faae13be78718fbfe8528dfcdc6335bfda1c105e73648d1dabcfb0b5a45691977bf1634320198f908dd118c090c
                                    identificacaoVotavel:
                                        codigo = 13
                                        partido = 13
                                    quantidadeVotos = 140
                                    tipoVoto = nominal
                                    assinatura = 88f633b1198297b34bd939fcdaf64e706028c43e3a83d2533f08ead4daafc7396c29d413e46693157f58c123e8f4edc00d4dd0282a385a23620313fd6ac0810d
                                    identificacaoVotavel:
                                        codigo = 22
                                        partido = 22
                                    quantidadeVotos = 143
                                    tipoVoto = nominal
                                    assinatura = ed59112c9b55b5a738a5a558448c11dd716a3b06d889ead53b7366c9d043c75c5fa2414380765c9c1ee046e3234ee41b1460a0513bd62eb17c082babec45620c
                                    quantidadeVotos = 8
                                    tipoVoto = nulo
                            ] <== votosVotaveis
                    ] <== totaisVotosCargo
            ] <== resultadosVotacao
    ] <== resultadosVotacaoPorEleicao
    urna:
        correspondenciaResultado:
            carga:
                codigoCarga = 257282375591450377973108
                dataHoraCarga = 20220925T153100
                numeroInternoUrna = 1635968
                numeroSerieFC = 3ba5839d
            identificacao = ('identificacaoSecaoEleitoral', {'municipioZona': {'municipio': 40029, 'zona': 179}, 'local': 1, 'secao': 57})
        numeroSerieFV = 6b76ae52
        tipoArquivo = votacaoUE
        tipoUrna = secao
        versaoVotacao = 8 26 0 0 - Onça-pintada
```

 Using a script you can process this file to generate a more convenient data. I use the previews command to generate a text clean file with the command: 
 ```
 python3 ./python/bu_dump.py -a spec/bu.asn1 -b bu/o00407-4002901790057.bu | tr "." " " >  bu2/o00407-4002901790057.bu.txt 
 ```

Running the following command on Linux you will have a csv: 
```
echo "municipio,zona,secao,eleitBiometria,eleitLibCod,idEleicao,eleitAptos,eleitCompa,LulaVotos,BolsoVotos,brancoVotos,nuloVotos,urna";grep  "InternoUrna\|codigo\|quantidade\|nulo\|branco\|tipoVoto\|municipio\|zona\|secao\|Biometrico\|LibCod\|idEleic\|Aptos\|Compar"  bu2/o00407-4853403420031.bu.txt | grep -v "cargo\|municipioZona\|iden\|Carga\|tipoU" |  awk "{ print \$3 }" | xargs | awk "{ print \$1,\",\",\$2,\",\",\$3,\",\",\$4,\",\",\$5,\",\",\$6,\",\",\$7,\",\",\$8,\",\",\$10,\",\",\$13,\",\",\$15,\",\",\$17,\",\",\$19}"
```

This will generate the output:
```
municipio,zona,secao,eleitBiometria,eleitLibCod,idEleicao,eleitAptos,eleitCompa,LulaVotos,BolsoVotos,brancoVotos,nuloVotos,urna
48534 , 342 , 31 , 35 , 8 , 545 , 255 , 157 , 124 , 24 , 1 , 8 , 1265507
```
To proccess all files is just a matter to batch this commands!

```
 echo "municipio,zona,secao,eleitBiometria,eleitLibCod,idEleicao,eleitAptos,eleitCompa,LulaVoto
s,BolsoVotos,brancoVotos,nuloVotos,urna" > csv/header.csv; for i in `ls -c1 bu2`; do grep  "InternoUrna\|codigo\|quantidade\|nulo\|branco\|tipoVoto\|municipio\|zona\|secao\|Biometrico\|LibCod\|idEleic\|Aptos\|Compar"  bu2/$i | grep -v "cargo\|municipioZona\|iden\|Carga\|tipoU" |  awk "{ print \$3 }" | xargs | awk "{ print \$1,\",\",\$2,\",\",\$3,\",\",\$4,\",\",\$5,\",\",\$6,\",\",\$7,\",\",\$8,\",\",\$10,\",\",\$13,\",\",\$15,\",\",\$17,\",\",\$19}" > csv/output.csv; done
```

```
 echo "municipio,zona,secao,QtdEleitBio,QtdEleitLibCod,idEleicao,QtdEleiApto,QtdComp,NumUrna,VotoLula,VotoBolsonaro,VotoNulo,VotoBranco,file" > header.csv;
for i in `ls -c1 `; do Lu=`grep "codigo = 13" -a2   $i | grep Votos | awk "{ print \\$3}"`;   if [[ ! $Lu ]] ; then  Lu=0;fi;
 Bo=`grep "codigo = 22" -a2   $i | grep Votos | awk "{ print \\$3}"`;    if [[ ! $Bo ]] ; then  Bo=0; fi; 
Br=`grep "tipoVoto = branco" -B1   $i  | grep Votos | awk "{ print \\$3}"`;   if [[ ! $Br ]] ; then Br=0; fi; 
Nu=`grep "tipoVoto = nulo" -B1   $i  | grep Votos | awk "{ print \\$3}"`;   if [[ ! $Nu ]] ; then  Nu=0; fi; 
grep  "InternoUrna\|municipio\|zona\|secao\|Biometrico\|LibCod\|idEleic\|Aptos\|Compar"  $i | grep -v "municipioZona\|tipoUrna" | awk "{ print \$3 }" | xargs |  awk "{ print \$1,\",\",\$2,\",\",\$3,\",\",\$4,\",\",\$5,\",\",\$6,\",\",\$7,\",\",\$8,\",\",\$9, \",\",$Lu, \",\", $Bo, \",\", $Br, \",\", $Nu, \",\",\"$i\" }" >> output.csv; done
```


```
for i in `ls -c1 `; do Lu=`head -52 $i  | grep "codigo = 13" -a2    | grep Votos | awk "{ print \\
$3}"`;   if [[ ! $Lu ]] ; then  Lu=0;fi;  Bo=`head -52 presidente $i | grep "codigo = 22" -a2   | grep Votos | awk "{ print \\$3}"`;    if [
[ ! $Bo ]] ; then  Bo=0; fi;  Br=`head -52 $i | grep "tipoVoto = branco" -B1   | grep Votos | awk "{ print \\$3}"`;   if [[ ! $Br ]] ; then
Br=0; fi;  Nu=`head -52 $i | grep "tipoVoto = nulo" -B1     | grep Votos | awk "{ print \\$3}"`;   if [[ ! $Nu ]] ; then  Nu=0; fi;  head -52 | grep  "InternoUrna\|municipio\|zona\|secao\|Biometrico\|LibCod\|idEleic\|Aptos\|Compar"   | grep -v "municipioZona\|tipoUrna" | awk "{ print \$3 }" | xargs |  awk "{ print \$1,\",\",\$2,\",\",\$3,\",\",\$4,\",\",\$5,\",\",\$6,\",\",\$7,\",\",\$8,\",\",\$9, \",\",$Lu, \",\", $Bo, \",\", $Br, \",\", $Nu, \",\",\"$i\" }" >> ../SP_output.csv; done
```

```
 for i in `ls -c1 /mnt/e/eleicoes2022/expanded/TO/o00407-9699700*.rdv`; do python3 python/rdv_dump.py -a spec/rdv.asn1 -r $i ; done
 
 for i in `dir -C1`; do 7zr x -y  -o"../log2/" $i >/dev/null; for files in `7zr l -y  $i |tail -n5 | grep -v "\-\-" | grep -v files | grep -v Name | awk "{ print \\$6 }"`;  do  mv ../log2/$files ../log2/$i-$files; done; done
 
  echo "" > pi-log-2votos-1min.txt;for i in `dir -C1 o00*`; do a=`grep -i "computado" $i | cut -c 1-17 | uniq -c | sort | grep "2 30" | wc -l`; b=`grep -i "computado" $i | cut -c 1-17 | uniq -c | sort | grep "1 30" | wc -l`;c=$(($a*100/($b+1)));echo "$a,$b,$c" >> pi-log-2votos-1min.txt; somaC=$(($somaC+$c));soma=$(($soma+1));done; echo $soma , $somaC ,$(($somaC/$soma));
  
  for i in `dir -C1 *.logjez`; do 7zr x -y  -o"../log2/" $i >/dev/null; for files in `7zr l -y  $i |tail -n5 | grep -v "\-\-" | grep -v files | grep -v Name | awk "{ print \\$6 }"`;  do  mv ../log2/$files ../log2/$i-$files; done; done
  
  find . -type f | xargs   grep Write | grep -v "favor\|Eleit\|dados\|prosse\|Vota\|Score\|sensor\|cancel\|captur\|ELEITO\|CARGO\|__\|pintada\|retornar\|Tenta\|Titu\|assinar\|Impresso\|\eleito\|compl\|txt" > write-error-ba-log.txt
  
  
  
```
