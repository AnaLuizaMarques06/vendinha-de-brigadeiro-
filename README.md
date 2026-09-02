# vendinha-de-brigadeiro-

<?php

class Produto
{
    public string $nome;
    public float $preco;
    public int $quantidade;

    public function calcularTotal(): float
    {
        return $this->preco * $this->quantidade;
    }
}


$produto1 = new Produto();
$produto1->nome = "Brigadeiro de leite ninho com Nutella";
$produto1->preco = 3.00;

$produto2 = new Produto();
$produto2->nome = "Brigadeiro de morango";
$produto2->preco = 3.00;

$produto3 = new Produto();
$produto3->nome = "Brigadeiro de maracujá";
$produto3->preco = 2.50;

$produto4 = new Produto();
$produto4->nome = "Brigadeiro de limão";
$produto4->preco = 2.50;

$produto5 = new Produto();
$produto5->nome = "Brigadeiro de paçoca";
$produto5->preco = 2.50;

$produto6 = new Produto();
$produto6->nome = "Brigadeiro de caramelo salgado";
$produto6->preco = 2.50;

$produto7 = new Produto();
$produto7->nome = "Brigadeiro de chocolate belga";
$produto7->preco = 3.00;

$produto8 = new Produto();
$produto8->nome = "Brigadeiro de frutas vermelhas";
$produto8->preco = 2.50;

$produto9 = new Produto();
$produto9->nome = "Brigadeiro de dois amores";
$produto9->preco = 2.50;

$produto10 = new Produto();
$produto10->nome = "Brigadeiro de mirtilo";
$produto10->preco = 2.50;


// Colocando todos os produtos em um array
$cardapio = [
    1 => $produto1,
    2 => $produto2,
    3 => $produto3,
    4 => $produto4,
    5 => $produto5,
    6 => $produto6,
    7 => $produto7,
    8 => $produto8,
    9 => $produto9,
    10 => $produto10
];

$totalCompra = 0;

echo "─────────────────────────── ୨୧ ──────────────────────────────\n";
echo "    ⋆˚࿔ 𝐯𝐞𝐧𝐝𝐢𝐧𝐡𝐚 𝐝𝐞 𝐛𝐫𝐢𝐠𝐚𝐝𝐞𝐢𝐫𝐨 𝜗𝜚˚⋆\n";
echo "                    ⏔⏔⏔ ꒰ ᧔ෆ᧓ ꒱ ⏔⏔⏔\n";
echo "                        \n    ";
echo "                    \n";
echo "             ° „ ★ 𝐂𝐀𝐑𝐃𝐀𝐏𝐈𝐎 🎀ྀིྀི\n";
echo "─────────────────────────── ୨୧ ──────────────────────────────\n";

foreach ($cardapio as $numero => $produto) {
    echo $numero . " - " . $produto->nome;
    echo " - R$ " . number_format($produto->preco, 2, ',', '.') . "\n";
}

echo "                    ⏔⏔⏔ ꒰ ᧔ෆ᧓ ꒱ ⏔⏔⏔\n";

do {

    echo "\n >ᴗ< Digite o número do brigadeiro que você deseja: ";
    $escolha = (int) trim(fgets(STDIN));


    if (!isset($cardapio[$escolha])) {
        echo "❌ Opção inválida! Escolha um número de 1 a 10.\n";
        continue;
    }

    $produtoEscolhido = $cardapio[$escolha];

    echo "Você escolheu: " . $produtoEscolhido->nome . "\n";

    echo "Digite a quantidade desejada: ";
    $quantidade = (int) trim(fgets(STDIN));

    if ($quantidade <= 0) {
        echo "❌ A quantidade precisa ser maior que zero.\n";
        continue;
    }

    $produtoEscolhido->quantidade = $quantidade;

    $totalProduto = $produtoEscolhido->calcularTotal();

    echo "\n૮꒰ ˶• ༝ •˶꒱ა ♡ Produto adicionado ao carrinho!\n";
    echo "ྀི Sabor: " . $produtoEscolhido->nome . "\n";
    echo "ྀི Quantidade: " . $quantidade . "\n";
    echo "ྀི Subtotal: R$ " . number_format($totalProduto, 2, ',', '.') . "\n";

    $totalCompra += $totalProduto;

    echo "\n 𐔌՞ ܸ.ˬ.ܸ՞𐦯Deseja comprar outro sabor? (s/n): ";
    $continuar = strtolower(trim(fgets(STDIN)));

} while ($continuar === "s");


echo "─────────────────────────── ୨୧ ──────────────────────────────\n";
echo "               𝐟𝐢𝐧𝐚𝐥 𝐝𝐚 𝐜𝐨𝐦𝐩𝐫𝐚\n";
echo "                   ⏔⏔⏔ ꒰ ᧔ෆ᧓ ꒱ ⏔⏔⏔\n";
echo " 𐔌՞ ܸ.ˬ.ܸ՞𐦯Total da compra: R$ " . number_format($totalCompra, 2, ',', '.') . "\n";
echo "            ≽^• ˕ • ྀི≼ Obrigada pela preferência! \n";

echo "─────────────────────────── ୨୧ ──────────────────────────────\n";

?>
