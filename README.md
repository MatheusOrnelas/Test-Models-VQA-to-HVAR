# Sistema de Identificação de Itens Fashion com VQA
Selection test for HVAR

## Introdução
Bem-vindo ao projeto de Visual Question Answering (VQA) para identificação de itens fashion em imagens. Este sistema foi desenvolvido para inovar a interação de marcas de moda europeias com seu público, utilizando machine learning para identificar itens fashions em mídias visuais e encontrar produtos similares.

## Contexto
Este projeto foi desenvolvido após um cliente do segmento fashion europeu expressar interesse em inovar sua interação com o público através de machine learning. A Hvar Consulting foi encarregada de desenvolver uma solução que permite identificar itens de moda em imagens ou vídeos e sugerir produtos similares do catálogo da empresa.

## Objetivo
Utilizaremos o dataset [SaffalPoosh/deepFashion-with-masks](https://huggingface.co/datasets/SaffalPoosh/deepFashion-with-masks) para treinar os modelos [ViLT](https://huggingface.co/docs/transformers/model_doc/vilt) e o modelo pré-treinado [BLIP](https://huggingface.co/Salesforce/blip-vqa-base). O modelo ViLT é voltado para uma análise mais categórica das imagens, enquanto o modelo BLIP para a identificação dos itens de forma mais contextual. Realizaremos um fine-tuning nesses modelos, ensinando o ViLT a identificar as categorias de roupas e o BLIP a descrever os itens e características das imagens de forma mais contextual.

## Requisitos
Realize a instalação das seguintes bibliotecas:
```bash
pip install datasets
pip install transformers[torch]
pip install accelerate -U
pip install gradio
pip install huggingface_hub
```

## Uso
### Detalhamento dos tópicos do notebook python `avaliacao.ipynb`

**- Instalação das Bibliotecas:** Instalação das bibliotecas necessárias para o projeto.

**- Análise prévia dos modelos pré-treinados:** Nesta etapa, é possível realizar análises e testes com os modelos que iremos realizar o fine-tuning. É possível submeter uma imagem e uma pergunta através da ferramenta Gradio e receber o output dos modelos no painel do Gradio. Estão à disposição no diretório `images` algumas imagens que foram utilizadas para esta avaliação e que ficaram de fora do fine-tuning dos modelos.

![Test01](/imgs_readme/test01.png)

**- Login Huggingface Hub:** É preciso realizar a autenticação com seu token gerado no [Hugging Face](https://huggingface.co/) para posteriormente realizarmos o push dos modelos para um repositório na plataforma.

**- Treinamento de Blip e ViLT:** Nesta etapa, realizamos os tratamentos necessários das imagens e textos, treinamos os modelos ViLT e BLIP e realizamos o push de cada um dos modelos para seus respectivos repositórios no Hugging Face.

**- Avaliação dos modelos após fine-tuning:** Nesta etapa, realizamos uma avaliação dos modelos após o fine-tuning utilizando a ferramenta Gradio para a avaliação, os testes podem ser realizados com as mesmas imagens do diretório `images` destacado na etapa **Análise prévia dos modelos pré-treinados**. Também já esta configurado para buscar os modelos ao qual, eu Matheus de Ornelas, realizei o treinamento e realizei o push dos modelos para o Hugging Face, estes são os repositórios dos dois modelos: [BLIP](https://huggingface.co/Ornelas/blip_finetuned_fashion) e [ViLT](https://huggingface.co/Ornelas/vilt_finetuned_fashion).

![Test02](/imgs_readme/test02.png)

## Resultados
Podemos observar que na primeira avaliação, o modelo ViLT não nos retornou nenhuma categoria, porém, após o fine-tuning, obtivemos bons resultados, mesmo que superficiais. Acreditamos que com alguns ajustes nos dados e adição de mais dados e ajuste de hiperparâmetros do modelo, é possível obter um resultado melhorado.
Em relação ao modelo BLIP, observamos que na primeira avaliação, o modelo também não retornava resultados satisfatórios iniciais. Então, após o fine-tuning do modelo, observamos um resultado muito bom. Mesmo com um modelo simples e com poucos dados, obtivemos resultados satisfatórios, onde conseguimos identificar uma quantidade significativa das categorias fashion nas imagens e com um contexto aceitável.

## Contribuição
Desenvolvido por Matheus de Ornelas Vasconcellos, este projeto reflete o compromisso em fornecer soluções inovadoras, utilizando tecnologias de ponta em machine learning e visão computacional.
Agradeço a oportunidade e o desafio proposto pelo Valerio Cardoso, colaborador da HVAR.

## Licença
Este projeto é licenciado sob os termos da Licença MIT. Isso permite que seja utilizado de maneira ampla, incluindo usos comerciais e modificativos, desde que seja dado o devido crédito ao desenvolvedor original, Matheus de Ornelas Vasconcellos, e aos contribuidores. A licença MIT é conhecida por sua permissividade e é uma das licenças de software mais populares no mundo open source.

Para mais detalhes sobre a licença, consulte o arquivo `LICENSE` no repositório do GitHub.
