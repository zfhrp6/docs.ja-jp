---
title: "Lifetime in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "static variables, lifetime"
  - "static variables, Visual Basic"
  - "declared elements, lifetime"
  - "Shared variable lifetime"
  - "lifetime, declared elements"
  - "lifetime, Visual Basic"
  - "lifetime"
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Lifetime in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言された要素の*有効期間*とは、その要素を使用できる期間です。  変数は、有効期間がある唯一の要素です。  このために、コンパイラでは、プロシージャ パラメーターおよび関数の戻り値が、変数の特別な例として扱われます。  変数の有効期間は、変数が値を保持できる期間を表します。  保持されている値は変わっても、有効期間中は常になんらかの値が保持されています。  
  
## さまざまな有効期間  
 \(プロシージャ外部の、モジュール レベルで宣言された\) *メンバー変数*は、通常、宣言された要素と同じ有効期間を持っています。  クラスまたは構造体で宣言された非共有変数は、宣言されたクラスまたは構造体の各インスタンスの別個のコピーとして存在します。  そのような各変数は、インスタンスと同じ有効期間を持っています。  ただし、共有 \(`Shared`\) 変数の有効期間は 1 つだけで、アプリケーションが終了するまで存続します。  
  
 \(プロシージャの内部で宣言された\) *ローカル変数*は、宣言されたプロシージャが実行されている間だけ存在します。  そのプロシージャのパラメーター、および関数の戻り値についても同様です。  ただし、プロシージャが他のプロシージャを呼び出した場合は、呼び出されたプロシージャの実行中もローカル変数の値は保持されます。  
  
## 有効期間の開始  
 ローカル変数の有効期間は、宣言されたプロシージャの制御が開始されるときに始まります。  すべてのローカル変数は、プロシージャの実行が開始されるとすぐに、データ型の既定値に初期化されます。  プロシージャは、初期値を指定する `Dim` ステートメントを検出すると、コードで他の値が既に割り当てられていたとしても、その初期値をローカル変数に設定します。  
  
 構造体変数の各メンバーは、独立した変数として初期化されます。  同様に、配列変数の各要素も個別に初期化されます。  
  
 プロシージャ内部のブロック内で宣言された変数 \(`For` ループなど\) は、そのプロシージャへのエントリ時点で初期化されます。  これらの初期化は、コードによってそのブロックが実行されるかどうかにかかわらず、有効になります。  
  
## 有効期間の終了  
 プロシージャが終了すると、ローカル変数の値は保持されず、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によってメモリが解放されます。  次にプロシージャを呼び出すときに、すべてのローカル変数が再度作成され、再初期化されます。  
  
 クラスまたは構造体のインスタンスが終了すると、非共有変数はメモリおよび値を失います。  クラスまたは構造体のそれぞれの新しいインスタンスによって、非共有変数が作成および再初期化されます。  しかし、`Shared` 変数はアプリケーションが実行を停止するまで保持されます。  
  
## 有効期間の延長  
 `Static` キーワードを持つローカル変数を宣言した場合、有効期間はプロシージャの実行時間よりも長くなります。  `Static` 変数が存在する長さが、どのようにプロシージャ宣言によって決定されるのかを、次の表に示します。  
  
|プロシージャの場所および共有|静的変数の有効期間の開始|静的変数の有効期間の終了|  
|--------------------|------------------|------------------|  
|モジュール内 \(既定で共有\)|プロシージャが最初に呼び出されたとき|アプリケーションの実行が停止されたとき|  
|クラスの `Shared` \(プロシージャはインスタンス メンバーではありません\)|特定のインスタンス、またはクラス名や構造体名自体のいずれかで、プロシージャが最初に呼び出されたとき|アプリケーションの実行が停止されたとき|  
|`Shared` ではなく、クラスのインスタンス \(プロシージャはインスタンス メンバーではありません\)|特定のインスタンスで、プロシージャが最初に呼び出されたとき|ガベージ コレクション \(GC\) に対して、インスタンスが解放されたとき|  
  
## 同じ名前の静的変数  
 複数のプロシージャで、同じ名前の静的変数を宣言できます。  これを実行すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のコンパイラは、このような各変数は別々の要素であると見なします。  いずれか 1 つの変数を初期化しても、その他の変数の値には影響しません。  これは、一連のオーバーロードを持つプロシージャを定義し、それぞれのオーバーロードで同じ名前の静的変数を定義した場合も同様です。  
  
## 静的変数のコンテナー要素  
 静的ローカル変数は、クラス内 \(つまりクラスのプロシージャの中\) で宣言できます。  ただし、構造体のメンバーまたはその構造体内部のプロシージャのローカル変数のいずれとしてでも、ローカルの静的変数を構造体内部で宣言することはできません。  
  
## 例  
  
### Description  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md) キーワードを使用して変数を宣言する例を、次に示します   \([Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) で、`Static` などの修飾子を使用している場合は、`Dim` キーワードは不要です\)。  
  
### コード  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/visualbasic/lifetime_1.vb)]  
  
### コメント  
 前の例では、変数 `applesSold` は、プロシージャ `runningTotal` が呼び出し元のコードに戻された後でも、引き続き存在します。  次に `runningTotal` が呼び出されたとき、`applesSold` は前に計算した値を保持しています。  
  
 `Static` を使用しないで `applesSold` が宣言された場合、は `runningTotal` が呼び出されても事前に蓄積された値は保持されません。  次に `runningTotal` が呼び出されたときに、`applesSold` は再作成され、0 に初期化されます。`runningTotal` は、呼び出されたときと同じ値を返すだけです。  
  
### コードのコンパイル  
 静的ローカル変数の値は、宣言の一部として初期化できます。  配列を `Static` として宣言する場合は、ランク \(次元数\)、各次元の長さ、および各要素の値を初期化できます。  
  
### セキュリティ  
 前の例では、`applesSold` をモジュール レベルで宣言して、同じ有効期間にできます。  ただし、この方法で変数のスコープを変更すると、プロシージャが変数に排他的にアクセスできなくなります。  この場合、他のプロシージャが `applesSold` にアクセスして値を変更する可能性があるため、現在の合計を信頼できなくなり、コードの管理が難しくなります。  
  
## 参照  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [Nothing](../../../../visual-basic/language-reference/nothing.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)