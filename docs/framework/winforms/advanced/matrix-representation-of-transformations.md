---
title: "変換の行列表現 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アフィン変換"
  - "複合変換"
  - "線形変換"
  - "行列"
  - "変換, 複合"
  - "変換, リニア"
  - "変換, 行列表現"
  - "変換, 変換"
  - "平行移動 (行列表現内の)"
  - "ベクター"
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 変換の行列表現
m×n 行列とは、m 行 n 列に配列された数値の集まりです。  いくつかの行列を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art04.png "AboutGdip05\_art04")  
  
 同じサイズの 2 つの行列を加算するには、個々の要素を加算します。  行列加算の 2 つの例を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art05.png "AboutGdip05\_art05")  
  
 m×n 行列に n×p 行列を掛け合わせることができ、その結果は m×p 行列になります。  1 番目の行列の列数が、2 番目の行列の行数と同じである必要があります。  たとえば、4 × 2 行列に 2 × 3 行列を掛け合わせて、4 × 3 行列を生成できます。  
  
 平面上の点および行列の行と列は、ベクターであると考えることができます。  たとえば、\(2, 5\) は 2 つの要素を持つベクターであり、\(3, 7, 1\) は 3 つの要素を持つベクターです。  2 つのベクターのドット積は、次のように定義されます。  
  
 \(a, b\) × \(c, d\) \= ac \+ bd  
  
 \(a, b, c\) × \(d, e, f\) \= ad \+ be \+ cf  
  
 たとえば、\(2, 3\) と \(5, 4\) のドット積は \(2\)\(5\) \+ \(3\)\(4\) \= 22 です。  \(2, 5, 1\) と \(4, 3, 1\) のドット積は \(2\)\(4\) \+ \(5\)\(3\) \+ \(1\)\(1\) \= 24 です。  2 つのベクターのドット積は、別のベクターではなく 1 つの数値になります。  また、ドット積を計算できるのは、2 つのベクターの要素の数が同じ場合だけです。  
  
 A\(i, j\) は、行列 A の i 行目、j 列目のエントリであるとします。  たとえば、A\(3, 2\) は行列 A の 3 行目、2 列目のエントリです。  A、B、および C の 3 つの行列があり、AB \= C であるとします。  C のエントリは次のように計算されます。  
  
 C\(i, j\) \= \(A の i 行\) × \(B の j 列\)  
  
 行列乗算のいくつかの例を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art06.png "AboutGdip05\_art06")  
  
 平面上の各点を 1 × 2 行列と考えると、その点を、2 × 2 行列を掛け合わせることによって変換できます。  点 \(2, 1\) に適用されるいくつかの変換を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art07.gif "AboutGdip05\_art07")  
  
 上の図に示す変換は、すべて線形変換です。  線形変換ではない平行移動などの変換は、2 × 2 行列による乗算では表現できません。  点 \(2, 1\) を 90°回転してから、x 方向に 3 単位、y 方向に 4 単位平行移動するとします。  この変換を実行するには、行列乗算の後で行列加算を実行します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art08.gif "AboutGdip05\_art08")  
  
 線形変換 \(2 × 2 行列による乗算\) の後で平行移動 \(1 × 2 行列の加算\) を実行することを、アフィン変換と呼びます。  1 つのアフィン変換を 2 つの行列 \(線形変換用の行列と平行移動用の行列\) の組み合わせに格納する代わりに、この変換全体を 1 つの 3 × 3 行列に格納できます。  この方法を使用するには、平面上の各点を、3 番目の座標としてダミー座標を持つ 1 × 3 行列に格納する必要があります。  通常の手法では、3 番目の座標はすべて 1 にします。  たとえば、点 \(2, 1\) を行列 \[2 1 1\] で表します。  アフィン変換 \(90°の回転、x 方向に 3 単位の平行移動、y 方向に 4 単位の平行移動\) を 1 つの 3 × 3 行列による乗算として表現する例を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art09.png "AboutGdip05\_art09")  
  
 上の例では、点 \(2, 1\) が点 \(2, 6\) に割り当てられます。  3 × 3 行列の 3 番目の列には、数値 0, 0, 1 が格納されています。  アフィン変換の 3 × 3 行列では、常にこの数値は同じです。  重要な数値は、列 1 と列 2 にある 6 個の数値です。  行列の左上の 2 × 2 部分が線形変換を表し、3 番目の行の最初の 2 つのエントリが平行移動を表します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art10.gif "AboutGdip05\_art10")  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、アフィン変換を <xref:System.Drawing.Drawing2D.Matrix> オブジェクトに格納できます。  アフィン変換を表す行列の 3 番目の列は常に \(0, 0, 1\) であるため、<xref:System.Drawing.Drawing2D.Matrix> を構築するときには、最初の 2 列にある 6 個の数値だけを指定します。  `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` ステートメントによって、上の図に示す行列が構築されます。  
  
## 複合変換  
 複合変換は、複数の変換を 1 つずつ連続して実行します。  次の一覧に示す行列と変換を考えてみます。  
  
|||  
|-|-|  
|行列 A|90°の回転|  
|行列 B|x 方向にファクター 2 のスケーリング|  
|行列 C|y 方向に 3 単位の平行移動|  
  
 行列 \[2 1 1\] で表される点 \(2, 1\) に A、B、C を順に掛け合わせると、点 \(2, 1\) に対して 3 つの変換が上の一覧の順序で適用されます。  
  
 \[2 1 1\]ABC \= \[\-2 5 1\]  
  
 複合変換の 3 つの部分を 3 つの異なる行列に格納する代わりに、A、B、C をすべて掛け合わせることで、この複合変換全体を格納する 1 つの 3 × 3 行列を得ることができます。  ABC \= D であるとします。  この場合、ある点に D を掛け合わせると、その点に A、B、C を順に掛け合わせた場合と同じ結果が得られます。  
  
 \[2 1 1\]D \= \[\-2 5 1\]  
  
 A、B、C、D の各行列を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art12.png "AboutGdip05\_art12")  
  
 個々の変換を表す行列を掛け合わせることにより、1 つの複合変換の行列を作成できるということは、連続するアフィン変換の任意の組み合わせを 1 つの <xref:System.Drawing.Drawing2D.Matrix> オブジェクトに格納できることを意味します。  
  
> [!CAUTION]
>  変換の順序が重要です。  一般に、回転、スケーリング、平行移動の順序で実行される変換は、スケーリング、回転、平行移動の順序で実行される変換と異なります。  同様に、行列乗算でも順序が重要です。  一般に、ABC と BAC は異なります。  
  
 <xref:System.Drawing.Drawing2D.Matrix> クラスには、複合変換を作成するためのメソッドとして、<xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>、<xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>、<xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>、<xref:System.Drawing.Drawing2D.Matrix.Scale%2A>、<xref:System.Drawing.Drawing2D.Matrix.Shear%2A>、および <xref:System.Drawing.Drawing2D.Matrix.Translate%2A> が用意されています。  30°の回転、y 方向にファクター 2 のスケーリング、x 方向に 5 単位の平行移動を順に実行する複合変換の行列の作成例を次に示します。  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 この行列を次の図に示します。  
  
 ![変換](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art13.png "AboutGdip05\_art13")  
  
## 参照  
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [マネージ GDI\+ での変換の使用](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)