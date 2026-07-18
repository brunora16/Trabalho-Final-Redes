# Análise de Roteamento BGP e Soberania Digital: EUA vs. China

Repositório destinado ao trabalho final da disciplina de **Redes de Computadores I** do curso de Ciência da Computação da Universidade Federal do Rio de Janeiro (UFRJ).

## Objetivo do Projeto
Este projeto analisa a infraestrutura de roteamento BGP (Border Gateway Protocol) no plano de controle de 10 gigantes da tecnologia (5 norte-americanas e 5 chinesas). O objetivo é investigar as diferenças na topologia de rede, grau de isolamento, dependência de trânsito e soberania digital, no contexto da rivalidade tecnológica global.

## Redes Analisadas (ASNs)
A amostra foi focada em grandes provedores de conteúdo e nuvem (Eyeballs/Stubs) para garantir o mapeamento completo das rotas na borda da Internet:

**China (CN):**
* `AS136907` - Huawei Cloud
* `AS45102` - Alibaba Cloud
* `AS132203` - Tencent
* `AS55990` - JD.com
* `AS38365` - Baidu

**Estados Unidos (US):**
* `AS8075` - Microsoft
* `AS15169` - Google
* `AS32934` - Meta (Facebook)
* `AS2906` - Netflix
* `AS13414` - X (Twitter)

## Métricas Extraídas
O código processa milhares de rotas públicas e extrai três métricas principais:
1. **Tamanho Médio do AS_PATH:** Mede a "distância" em saltos lógicos (ASes) para alcançar as redes.
2. **Concentração Top-5 (%):** Mede a dependência das empresas em relação aos seus 5 maiores provedores de trânsito diretos (gargalo de rede).
3. **Soberania Digital (Fração de ASes Estrangeiros %):** Mede a proporção do tráfego internacional de cada rede que obrigatoriamente transita por Sistemas Autônomos registrados em países diferentes de sua sede.

## Metodologia e Fontes de Dados
O pipeline de dados foi construído em Python (Jupyter Notebook) e consulta dinamicamente as seguintes bases acadêmicas e oficiais:
* **RIPEstat (Data API):** Utilizado para extrair os caminhos BGP (`/data/bgp-state/`) e garantir as informações de registro soberano oficial (`/data/rir-geo/`).
* **PeeringDB / RDAP:** Utilizados como endpoints de segurança e validação secundária para o mapeamento da localização geográfica dos ASNs de trânsito.

### Como Executar o Projeto (Google Colab)

Como o pipeline de dados foi desenvolvido e validado no ambiente em nuvem do Google Colab, não é necessária nenhuma configuração de ambiente local ou instalação via terminal.

Para reproduzir os resultados:
1. Faça o download do arquivo `Trabalho_Redes.ipynb` presente neste repositório.
2. Acesse o [Google Colab](https://colab.research.google.com/).
3. Execute as células em ordem sequencial. O script fará as consultas via API em tempo real e gerará os arquivos de métricas e gráficos diretamente no armazenamento temporário da sua sessão do Colab.

## Resultados
Os dados tabulados (`.csv`) e os três gráficos de análise comparativa gerados pelo script encontram-se disponíveis na raiz deste repositório para consulta.
