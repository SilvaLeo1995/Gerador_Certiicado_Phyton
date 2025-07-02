**GERADOR AUTOMÁTICO DE CERTIFICADOS COM PYTHON**

Este projeto foi desenvolvido com fins **educacionais**, como parte de um **curso gratuito de Python** ministrado pelo **Prof. Sauer** entre os dias **27/05/2025 e 28/05/2025**.  
O objetivo principal é mostrar, na prática, como **automatizar tarefas com Python**, como:

- Leitura de arquivos com dados (CSV)
- Manipulação de texto e geração de arquivos
- Criação de documentos em PDF com formatação personalizada

- **TECNOLOGIAS E BIBLIOTECAS UTILIZADAS**

- Para tornar essa automação possível, foram utilizadas duas bibliotecas essenciais:

- **Pandas**
- - Biblioteca poderosa para **manipulação de dados tabulares**.
- Usada para ler o arquivo `dados.csv`, que contém os nomes dos participantes.
- Permite percorrer os dados de forma simples e eficiente.

**COMO FUNCIONA O PROJETO**

realiza as seguintes etapas:

**1.** - Carrega os dados dos participantes de um arquivo chamado dados.csv.

**2.** - Define o conteúdo fixo do certificado, como título, texto descritivo e nome do professor.

**3.** - Percorre cada nome da lista e gera um arquivo PDF individual com o nome personalizado.

**4.** - Adiciona um fundo personalizado (template.png) que simula um certificado real.

**5.** Salva os arquivos em PDF com nomes como: Certificado_NomeCompleto.pdf.

**EXECUÇÃO**

import pandas as pd
from fpdf import FPDF

dados = pd.read_csv("dados.csv")

# Informações fixas
titulo = "CERTIFICADO DE PARTICIPAÇÃO"
subtitulo = "Este certificado comprova que"
texto2 = "concluiu com êxito o curso GRATUITO DE PYTHON ministrado por"
texto3 = "PROF. SAUER entre 27/05/2025 e 28/05/2025,"
texto4 = "com carga horária de aproximadamente 08 horas."

# Geração dos certificados
for nome in dados['nomecompleto']:
    pdf = FPDF()
    pdf.add_page()
    pdf.set_font("Arial", 'B', size=15)
    pdf.image("template.png", x=0, y=0)

    pdf.text(65, 95, titulo)
    pdf.text(67, 120, subtitulo)
    pdf.text(70, 145, nome)
    pdf.text(20, 165, texto2)
    pdf.text(50, 175, texto3)
    pdf.text(50, 185, texto4)

    pdf.output(f"Certificado_{nome}.pdf")

**RESULTADO ESPERADO**

Para cada nome listado no arquivo dados.csv, um PDF individual é criado com o nome da pessoa, pronto para ser impresso ou enviado por e-mail.

**AUTOR**

Leonardo Gabriel Silva
Este projeto foi desenvolvido como parte prática de um minicurso de Python.
