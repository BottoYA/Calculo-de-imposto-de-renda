// Calcular o imposto de renda retido na fonte(IRRF)mensalmente de um grupo de contribuintes 
#include<stdio.h>
#include<math.h>
int main()
{
    int imposto_renda, cpf, dependentes, contribuintes, i;
    float aliquota, deducao, desconto, renda_mensal, valor, valor_final, total, desconto_irrf, desconto_inss, desconto_inss_1, base;

    // Entrada de dados

      printf("*** Entrada de dados do Contribuinte\n Digite o numero de CPF: ", i);
      scanf("%d", &cpf);

      printf("\n De o numero de dependentes: ");
      scanf("%d", &dependentes);

      printf("\n De o valor da renda mensal: ");
      scanf("%f", &renda_mensal);

    // Calculo do desconto do INSS

    valor = dependentes * 189.59;

    if (renda_mensal <= 1302)
    {
        aliquota = 0.075;
        deducao = 0;
    }

    if (renda_mensal > 1302 && renda_mensal <= 2571.29)
    {
        aliquota = 0.09;
        deducao = 19.53;
    }

    if (renda_mensal > 2571.30 && renda_mensal <= 3856.94)
    {
        aliquota = 0.12;
        deducao = 96.67;
    }

    if (renda_mensal > 3856.95 && renda_mensal <= 7507.49)
    {
        aliquota = 0.14;
        deducao = 173.80;
    }

    if (renda_mensal > 7507.50)
    {
        desconto = 877.22;
    }

    // CALCULO do desconto E SAIDA DE RESULTADOS do INSS

    if (renda_mensal < 7507.50)
    {
    desconto_inss_1 = renda_mensal * aliquota;
    desconto_inss = desconto_inss_1 - deducao;
    printf("\n O desconto do INSS sera de: %.2lf reais", desconto_inss);
    }

    if (renda_mensal > 7507.50)
    {
    desconto_inss = renda_mensal - desconto;
    printf("\n O desconto do INSS sera de: %.2lf reais", desconto_inss);
    }

    base = renda_mensal - desconto_inss - valor;

    //Calculo do IRRF

    total = renda_mensal - desconto_inss;

    if (base > 1903.99 && base <= 2826.65)
    {
        aliquota = 0.075;
        deducao = 142.80;
    }

    if (base >  2826.66 && base <= 3751.05)
    {
        aliquota = 0.15;
        deducao = 354.80;
    }

    if (base >  3751.06 && base <= 4664.68)
    {
        aliquota = 0.225;
        deducao = 636.13;
    }

    if (base >  4664.68)
    {
        aliquota = 0.275;
        deducao = 869.36;
    }

    if (base <= 1903.98)
    {
        printf("\n***Esse colaborador esta isento de desconto de imposto de renda, logo seu salario descontado sera de: %.2lf\n", total);
    }

    total = 0;
    total = base * aliquota;
    desconto_irrf = total - deducao;

    printf("\n O valor de desconto do IRRF sera de: %.2lf\n", desconto_irrf);

    valor_final = renda_mensal - desconto_inss - desconto_irrf;

    printf("\n***Salario (descontando IRRF e INSS) sera de: %.2lf", valor_final);
    printf("\n\n***Calculo de Imposto de Renda concluido.\n");

        return 0;
}
