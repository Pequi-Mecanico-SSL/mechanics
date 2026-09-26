# Pequi Mecânico SSL — Mechanics

Modelos de componentes e desenhos dimensionais para integração mecânica do robô SSL-EL. Seleção revisada em 26/09/2026 a partir dos nove arquivos fornecidos pela equipe.

## Componentes para a montagem

Importar os modelos de `components/` no CAD do chassi. As quantidades indicadas são por robô; os arquivos não constituem uma montagem completa nem comprovam encaixes e folgas.

| Modelo | Qtd. | Utilização e conferência necessária |
| --- | ---: | --- |
| [Raspberry Pi 4 Model B](components/raspberry-pi-4-model-b.step) | 1 | Computador embarcado: suporte, acesso aos conectores e espaço para o HAT. [Desenho dimensional](references/raspberry-pi-4-model-b-dimensions.pdf). |
| [ST B-G431B-ESC1](components/st-b-g431b-esc1.step) | 4 | Controlador de cada motor: suporte, ventilação e cabos. Conferir se a placa destacável ST-LINK/BEC permanece no conjunto real. |
| [Nanotec DF45L024048-A](components/nanotec-df45l024048-a.step) | 4 | Motor de cada roda: fixação, posição e acoplamento ao cubo. |
| [GTF omniwheel 50 mm v4](components/gtf-omniwheel-50mm-v4.step) | 4 | Referência de roda omnidirecional: interferências, cubo e folga dos roletes. O projeto documenta rodas de 50 mm, mas a marca/revisão deste modelo precisa ser conferida na peça real. |
| [Pololu MinIMU-9 v5](components/pololu-minimu-9-v5.step) | 1 | Suporte da IMU: orientação dos eixos e acesso à fiação I2C. |
| [Waveshare RS485 CAN HAT](components/waveshare-rs485-can-hat.step) | 1 | Montagem sobre a Raspberry Pi: espaçadores, altura e saída dos cabos CAN. Conferir revisão da placa. |

As funções foram confrontadas com o TDP 2026 fornecido localmente e os repositórios [motor-controller](https://github.com/Pequi-Mecanico-SSL/motor-controller) e [pequi_ssl_el](https://github.com/Pequi-Mecanico-SSL/pequi_ssl_el). O [código de cinemática](https://github.com/Pequi-Mecanico-SSL/pequi_ssl_el/blob/3afe7e71667017f5217aa777948763932293336f/src/robot_control/robot_control/kinematics.py) usa raio efetivo de roda de 24,5 mm; não alterar essa calibração apenas pelo nome nominal de 50 mm do modelo.

## Referências candidatas

Estes três arquivos são úteis para estudar fixações e passagem de cabos, mas sua adoção no robô ainda não está confirmada.

| Referência | Utilização e limite |
| --- | --- |
| [MR60PB-M-G-Y de 3 pinos](references/candidates/mr60pb-m-g-y-3pin.step) | Candidato para conexão das fases do motor. Conferir versão para placa, conector complementar e espaço para os cabos. |
| [XT90 macho](references/candidates/xt90-male.ipt) | Candidato para conexão de alimentação. Único modelo fornecido: Autodesk Inventor IPT; não há STEP e a geometria deste arquivo não foi validada. Para uso em outro CAD, exportar em software compatível. |
| [Solenoide SOLETEC 018](references/candidates/soletec-018-solenoid-dimensions.pdf) | Desenho mecânico na posição energizada: corpo de 33 × 22 × 15 mm e comprimento total de 59,5 ± 1,0 mm. Não informa tensão, força, resistência, curso completo ou ciclo de trabalho; não comprova equivalência ao solenoide customizado de 200 V citado no TDP. |

## Verificação

Os quatro ZIPs de origem passaram na verificação CRC de todas as entradas. Os sete STEP selecionados foram importados no FreeCAD 1.1.1 e passaram em `Shape.isValid()`, com geometria não vazia. Os dois PDFs foram renderizados e inspecionados. O IPT teve integridade da entrada ZIP conferida, mas não foi aberto no Inventor.

| Modelo STEP | Sólidos | Envelope X × Y × Z (mm) |
| --- | ---: | --- |
| Raspberry Pi 4B | 109 | 88,990 × 19,900 × 58,400 |
| ST B-G431B-ESC1 | 749 | 31,000 × 42,050 × 16,485 |
| Nanotec DF45L024048-A | 34 | 45,022 × 63,011 × 47,600 |
| GTF omniwheel 50 mm v4 | 89 | 48,459 × 49,200 × 12,601 |
| Pololu MinIMU-9 v5 | 1 | 20,320 × 12,700 × 2,216 |
| Waveshare RS485 CAN HAT | 95 | 65,022 × 30,022 × 18,500 |
| MR60PB-M-G-Y | 1 | 9,100 × 20,300 × 17,300 |

Os envelopes seguem a orientação original de cada modelo e incluem os detalhes modelados. Não equivalem necessariamente às dimensões nominais da placa. A validação geométrica não comprova correspondência com a peça real, montagem sem interferências ou desempenho elétrico.

## Seleção e nomes

Os modelos foram extraídos ou copiados sem alterar seu conteúdo; somente os nomes externos foram padronizados. Os originais permanecem fora do repositório.

| Origem fornecida | Arquivo(s) aproveitado(s) |
| --- | --- |
| `raspberry-pi-4-model-b-1.snapshot.3.zip` | `Raspberry Pi 4 Model B.STEP` → `components/raspberry-pi-4-model-b.step`; `Raspberry Pi 4 Model B Dimensions.pdf` → `references/raspberry-pi-4-model-b-dimensions.pdf` |
| `B-G431B-ESC1.step` | `components/st-b-g431b-esc1.step` |
| `GTF Robots 50mm Wheel v4.step` | `components/gtf-omniwheel-50mm-v4.step` |
| `DF45L024048-A(1).stp` | `components/nanotec-df45l024048-a.step` |
| `solenoide 557 018.pdf` | `references/candidates/soletec-018-solenoid-dimensions.pdf`; modelo 018 identificado no desenho |
| `mr60pb-m-g-y-1.snapshot.1.zip` | `mr60pb-mgy_3pin.stp` → `references/candidates/mr60pb-m-g-y-3pin.step` |
| `xt90-male-plug-1.snapshot.2.zip` | `XT90 Male.ipt` → `references/candidates/xt90-male.ipt` |
| `minimu-9-v5-gyro-accelerometer-and-compass-lsm6ds33-and-lis3mdl-carrier.step` | `components/pololu-minimu-9-v5.step` |
| `RS485_CAN_HAT_3D_Drawing.zip` | `RS485_CAN_HAT_3D_Drawing/RS485_CAN_HAT.stp` → `components/waveshare-rs485-can-hat.step` |

Foram omitidos os ZIPs completos, imagens de apresentação, a montagem/peças SolidWorks e Parasolid da Raspberry Pi e os auxiliares `t19-3.stp`/`t19-3.prt.19` do HAT. Os STEP principais já permitem o estudo de posicionamento; os formatos omitidos permanecem nos downloads originais caso seja necessária edição nativa detalhada.

Para conferir a integridade dos dez arquivos selecionados, executar na raiz do repositório:

```sh
sha256sum -c SHA256SUMS
```

Os arquivos de terceiros foram fornecidos pela equipe sem URLs de origem ou licenças anexas identificadas. Nenhuma nova licença é atribuída a esses modelos.
