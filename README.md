# Testes de Desempenho - Reqres API com Apache JMeter

Este repositório contém os planos de teste e relatórios para avaliar o desempenho da API Reqres utilizando o Apache JMeter. Os testes incluem cenários de carga e estresse para os endpoints fornecidos.

## **Configuração do Ambiente**

### **Instalação do Apache JMeter**
1. Faça o download do [JMeter](https://jmeter.apache.org/download_jmeter.cgi).
2. Extraia os arquivos e adicione o diretório bin ao PATH.
3. Execute o JMeter:
   - Windows: `jmeter.bat`
   - Linux/Mac: `jmeter.sh`

---

## **Cenários de Teste**

### **Teste de Carga**
- **Objetivo**: Simular 100 usuários simultâneos fazendo requisições ao endpoint GET `/api/users?page=2`.
- **Configurações**:
  - Threads: 100 usuários.
  - Ramp-Up: 10 segundos.
  - Critérios:
    - Tempo médio de resposta < 2 segundos.
    - Taxa de erro < 1%.
- **Relatórios Gerados**:
  - `reports/load-test-summary.html`

---

## **Como Executar**

1. Clone o repositório:
   ```bash
   git clone https://github.com/hebroms/testesCarga.git
   cd reqres-performance-tests
   ```
2. Abra os planos de teste no JMeter:

   ```bash
   jmeter -t test-plans/load-test.jmx
   ```
3. Clique no botão de execução no JMeter para rodar os testes.

OU

   ```bash
   jmeter -n -t test-plans/load-test.jmx -l reports/load-test-results.jtl -e -o reports/load-test-report
   ```
