# Corne 

Repo que contem tudo para o corne (incluindo um tutorial de como fazer flash neste inferno)

## 📂 Layouts

Contem layouts feitos no QMK configurator, em JSON.
Para transformar esses layouts num keymap.c, correr o comando no QMK MSYS: `qmk json2c {keymap}`

## ⚡ Flashing

Para passar o layout para o corne, precisamos de transformar o layout para .uf2.

Para isso precisamos de passar o `layout.json` para um `keymap.c`, e depois compilar para `.uf2`.

O primeiro passo pode ser usado com o comando `qmk json2c {keymap}`. Esta maneira nunca funciona, então podemos usar esta ferramenta com o mesmo propósito -> https://jhelvy.shinyapps.io/qmkjsonconverter/

Com o `keymap.c` temos quase tudo pronto para a compilação. Só precisamos de criar uma nova pasta em ...qmk_firmware/keyboards/crkbd/keymaps. Esta pasta deve ter o nome do layout que queremos fazer.

Depois copiamos os ficheiros `rules.mk` e `config.h` de outro layout para dentro da pasta que fizemos.

Opcionalmente, podemos editar o `keymap.c` de modo a configurar mais coisas sem ser o layout. Como por exemplo um tacómetro de WPM ou a Luna, o caozinho.

O segundo passo é o comando `compile` normal, com a adenda de que o ficheiro `rules.mk` precisa de ter descrita a flag `CONVERT_TO=promicro_rp20400`. Esta flag é o que faz o processo de compilação gerar um ficheiro `.uf2`.

`compile -kb crkbd -km <nome_do_layout>`

Depois disso, basta fazer reset às duas metades. Elas irão definir-se como um disco/pen, onde podemos arrastar o ficheiro que fizemos. Tem que se arrastar o mesmo ficheiro para as duas metades, mas convem fazer uma de cada vez.