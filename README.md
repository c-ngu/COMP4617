# COMP4617
COMP4617 Group Project

## Prerequiste 
Ensure that Java is 21.x+
Maven is 3.9 or 4

Install and setup codeQL, downloading the latest:
```
codeql-bundle-linux64.tar.zst
```

extract the file 
```
codeql-bundle-linux64.tar.zst
```

## Clone the CodeQL starter workspace
```
git clone --recursive https://github.com/github/vscode-codeql-starter.git
```

Pull and update the latest standard
```
git pull
git submodule update --recursive
```


# Creating the database

```
# Certificate expired - bypass that test | This command only works for java library, change the language to the respective library language
codeql database create ~/COMP4617/COMP4617/codeql-database/<LIBRARY NAME> --language=java-kotlin --command="mvn clean install -DskipTests"


```


# After creating the database/query, run it
```
codeql database analyze ~/COMP4617/COMP4617/codeql-database/lib-crypto-util java-security-and-quality.qls --format=sarif-latest --output=codeql-results.sarif
```

codeql database analyze ~/COMP4617/COMP4617/codeql-database/tink-java java-security-and-quality.qls --format=sarif-latest --output=codeql-results.sarif


# Uplaoding Results
```
codeql github upload-results --repository=c-ngu/COMP4617 --ref=refs/heads/main --commit=$(git rev-parse HEAD) --sarif=codeql-results.sarif

#Double cecking what CodeQL actually put into the SARIF
sudo apt install jq
jq '.runs[] | {tool: .tool.driver.name, rules: (.tool.driver.rules | length), results: (.results | length)}' codeql-results.sarif
```
