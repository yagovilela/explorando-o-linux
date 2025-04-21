# Explorando o Linux - Estrutura e Organização de Pastas

Este repositório faz parte da minha jornada de aprendizado em Linux e DevOps. Aqui, recriei e reorganizei uma estrutura de diretórios e arquivos utilizando apenas comandos de terminal, simulando um ambiente organizacional.

---

## Objetivo

Praticar comandos essenciais do terminal Linux para:

- Criar e navegar entre diretórios
- Criar arquivos vazios
- Copiar, mover e remover pastas e arquivos
- Utilizar caminhos relativos e absolutos
- Reorganizar estruturas de arquivos conforme mudanças de requisitos

---

## Cenário Simulado

Você foi contratado para configurar a estrutura de arquivos da empresa fictícia **CompanyA** em uma máquina Linux. Após algumas semanas, a estrutura precisou ser reorganizada.

---

## Estrutura Inicial Criada (Task 2)

/home/ec2-user/CompanyA/ ├── Finance/ │ ├── ProfitAndLossStatements.csv │ └── Salary.csv ├── HR/ │ ├── Assessments.csv │ └── TrialPeriod.csv └── Management/ ├── Managers.csv └── Schedule.csv

---

## Reorganização da Estrutura (Task 3)

/home/ec2-user/CompanyA/ └── HR/ ├── Finance/ │ ├── ProfitAndLossStatements.csv │ └── Salary.csv ├── Management/ │ ├── Managers.csv │ └── Schedule.csv └── Employees/ ├── Assessments.csv └── TrialPeriod.csv

---

## Comandos Utilizados

```bash
# Criação da estrutura
mkdir CompanyA && cd CompanyA
mkdir Finance HR Management
cd HR && touch Assessments.csv TrialPeriod.csv && cd ..
cd Finance && touch Salary.csv ProfitAndLossStatements.csv && cd ..
touch Management/Managers.csv Management/Schedule.csv

# Reorganização
cd /home/ec2-user/CompanyA
cp -r Finance HR
rm Finance/ProfitAndLossStatements.csv Finance/Salary.csv
rmdir Finance
mv Management HR
cd HR
mkdir Employees
mv Assessments.csv TrialPeriod.csv Employees/

# Verificação
ls -laR

Aprendizados
Estruturação de projetos no Linux

Comandos mkdir, touch, cd, ls, cp, rm, mv, rmdir

Uso de caminhos relativos e absolutos

Manipulação segura de arquivos e diretórios
