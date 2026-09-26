# COMP4617
COMP4617 Group Project

## Prerequiste 
Ensure that Java is 21.x+
Maven is 3.9 or 4

Install and setup codeQL, downloading the latest:
'''
codeql-bundle-linux64.tar.zst
'''

extract the file 
'''
codeql-bundle-linux64.tar.zst
'''

## Clone the CodeQL starter workspace
'''
git clone --recursive https://github.com/github/vscode-codeql-starter.git
'''

Pull and update the latest standard
'''
git pull
git submodule update --recursive
'''



Certificate expired - bypass that test
codeql database create ~/codeql-databases/lib-crypto-util --language=java-kotlin --command="mvn clean install -DskipTests"

~/COMP4617/COMP4617/codeql-database/lib-crypto-util


# After creating the database/query, run it
```
codeql database analyze ~/COMP4617/COMP4617/codeql-database/lib-crypto-util java-security-and-quality.qls --format=sarif-latest --output=codeql-results.sarif
```