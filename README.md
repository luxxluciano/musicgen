# musicgen
Pythons Jazz Music Generator
🎸 **Gambaleando: Uma Jornada Musical** 🎶

✨ Baseado na genialidade de Frank Frankeado, nossa música é uma fusão de estilos que vai além dos limites do convencional. Do lendário shred Shredado ao misterioso Ghost Ghosteado, cada nota é uma expressão de arte. Seja envolvido pela magia de Little Charmer ou embarque em uma viagem através dos Passages Passageados.

🎵 **Harmonia Deslumbrante:**

(Com indicação de compasso)

Compasso 1: (G - Bm - F)
Nota Melódica: G - C - F

Compasso 2: (F - Cm - G)
Nota Melódica: F - B♭ - E

Compasso 3: (Dm - Am - E - B)
Nota Melódica: D - G - C - F#

Em termos de tonalidade, considerando o acorde mais comum ou principal, a música pode ser interpretada em G maior. No entanto, é importante notar que há variações de acordes menores (Bm, Cm, Dm, Am) que podem indicar uma modulação ou mudança temporária na tonalidade. Se a música permanecer principalmente em G maior, então essa seria a tonalidade principal.

```python
import streamlit as st
import time
import random
from pysynth_b import make_wav
from pydub import AudioSegment
from pydub.playback import play

# Função para gerar uma nota aleatória na escala jazzística de quartas (1-4-7)
def generate_random_jazz_note(root_note):
    intervals = [0, 3, 6]  # Intervalos da escala jazzística de quartas
    return [root_note + interval for interval in intervals]

# Função principal do aplicativo
def main():
    st.title("Improvisação Melódica em Quartas - Estilo Jon Coltrane")

    # Definindo a harmonia
    harmony = [("G", "Bm", "F"), ("F", "Cm", "G"), ("Dm", "Am", "E", "B")]

    # Loop principal
    for compasso, acordes in enumerate(harmony, start=1):
        st.write(f"Compasso {compasso}: {acordes}")

        for acorde in acordes:
            root_note = ord(acorde[0].lower()) - 96  # Convertendo a nota para um número (A=1, B=2, ..., G=7)
            melody_note = generate_random_jazz_note(root_note)
            melody_notes = [chr(note + 96).upper() for note in melody_note]

            st.write(f"Nota Melódica: {' - '.join(melody_notes)}")

            # Converter as notas para a sintaxe aceita pelo PySynth
            melody_notes = [f"{note}{octave}" for note in melody_notes for octave in ['1', '2', '4', '8']]

            # Gerar o arquivo de áudio para o compasso atual
            make_wav(melody_notes, fn=f"compasso_{compasso}_acorde_{acorde}.wav", leg_stac=50)

            # Reproduzir o áudio do arquivo gerado usando PyDub
            audio = AudioSegment.from_wav(f"compasso_{compasso}_acorde_{acorde}.wav")
            play(audio)

            # Adicionar um pequeno atraso para simular a execução em tempo real
            time.sleep(2)  # Aumentando o tempo de atraso para permitir a reprodução completa do áudio

# Inicia o aplicativo
if __name__ == "__main__":
    main()
```

Neste script, além de exibir as informações sobre os acordes e as melodias geradas, também geramos arquivos de áudio para cada compasso e os reproduzimos diretamente no aplicativo usando a biblioteca PyDub. Certifique-se de ter a biblioteca PySynth instalada (`pip install pysynth-b`) para que o código funcione corretamente.


A parte do código que imita o estilo de John Coltrane é a maneira como as notas melódicas são geradas e manipuladas. John Coltrane era conhecido por sua habilidade de improvisação e por sua exploração de padrões cromáticos e modais. 

No código fornecido, a função `generate_random_jazz_note(root_note)` gera notas aleatórias na escala jazzística de quartas (1-4-7). Esta escala é comum no jazz e fornece um som característico usado por muitos músicos desse gênero, incluindo John Coltrane.

Além disso, as notas são convertidas em diferentes durações (minimas, seminimas, fusas e semifusas) através do uso dos argumentos `['1', '2', '4', '8']` na linha `melody_notes = [f"{note}{octave}" for note in melody_notes for octave in ['1', '2', '4', '8']]`. Isso adiciona variação rítmica às melodias, o que é uma característica comum nos solos de saxofone de John Coltrane e outros músicos de jazz.

Assista ao clip [aqui]
(src=https%3A%2F%2Fwww.facebook.com%2FBananaMachinada%2Fposts%2Fpfbid0288UboEzKGLKVFGu3Wc2wJzWAWvN1JErbwUYF75Hi2xW2p6oTq88DDakAXhzm9m4fl)
 

