#include <stdio.h>
#include <stdbool.h>

// Função para verificar se todos os pontos foram atingidos
bool todosPontosAtingidos(int *pontos, int N) {
    for (int i = 0; i < N; i++) {
        if (pontos[i] == 0) {
            return false;
        }
    }
    return true;
}

int main() {
    int N;
    scanf("%d", &N);

    int pontos[N];
    for (int i = 0; i < N; i++) {
        pontos[i] = 0;
    }

    int ciclo[2 * N];
    for (int i = 0; i < 2 * N; i++) {
        scanf("%d", &ciclo[i]);
    }

    int soldasNecessarias = 0;
    for (int i = 0; i < 2 * N; i++) {
        if (pontos[ciclo[i] - 1] == 0) {
            pontos[ciclo[i] - 1] = 1;
        }
        if (todosPontosAtingidos(pontos, N)) {
            soldasNecessarias = i + 1;
            break;
        }
    }

    if (soldasNecessarias > 0) {
        printf("%d\n", soldasNecessarias);
    } else {
        printf("0\n");
    }

    return 0;
}
