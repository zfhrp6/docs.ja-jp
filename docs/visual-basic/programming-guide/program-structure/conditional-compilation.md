---
title: "Conditional Compilation in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional compilation, about conditional compilation"
  - "compilation, conditional"
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conditional Compilation in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

条件付きコンパイルでは、プログラムの特定のコード ブロックだけを選択してコンパイルできます。プログラムの他の部分は無視されます。  
  
 たとえば、同じプログラミング タスクに対する異なるアプローチについて速度を比較するデバッグ ステートメントを記述する場合や、アプリケーションを混合言語にローカライズする場合などがあります。  条件付きコンパイル ステートメントは、実行時ではなくコンパイル時に実行されます。  
  
 条件に基づいてコンパイルするコードのブロックを指定するには `#If...Then...#Else` ディレクティブを使用します。  たとえば、同じソース コードからフランス語バージョンおよびドイツ語バージョンのアプリケーションを作成するには、定義済みの定数 `FrenchVersion` および `GermanVersion` を使用して、プラットフォーム固有のコードを `#If...Then` ステートメントの中に記述します。  この方法を次の例で示します。  
  
 [!CODE [VbVbalrConditionalComp#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#5)]  
  
 コンパイル時に条件付きコンパイル定数 `FrenchVersion` の値を `True` に設定すると、フランス語バージョンの部分のコードがコンパイルされます。  定数 `GermanVersion` の値を `True` に設定すると、ドイツ語バージョンのコードがコンパイルされます。  どちらの値も `True` に設定しない場合は、最後の `Else` ブロックのコードが実行されます。  
  
> [!NOTE]
>  コードが現在の分岐の一部ではない場合、コードの編集時、および条件付きコンパイル ディレクティブの使用時に、オートコンプリートは機能しません。  
  
## 条件付きコンパイル定数の宣言  
 条件付きコンパイル定数は、次の 3 つのいずれかで設定できます。  
  
-   **プロジェクト デザイナー**  
  
-   コマンド ライン \(コマンド ライン コンパイラを使用する場合\)  
  
-   コード内  
  
 条件付きコンパイル定数は特殊なスコープを持つため、標準のコードからアクセスすることはできません。  条件付きコンパイル定数のスコープは、定数の設定方法によって異なります。  次の表は、上記の 3 つの方法を使って宣言した定数のスコープを示しています。  
  
|||  
|-|-|  
|定数の設定方法|定数のスコープ|  
|**プロジェクト デザイナー**|プロジェクト内のすべてのファイルに対してパブリック|  
|コマンド ライン|コマンド ライン コンパイラに渡されたすべてのファイルに対してパブリック|  
|コード内の `#Const` ステートメント|宣言されたファイル内でプライベート|  
  
||  
|-|  
|プロジェクト デザイナーで定数を設定するには|  
|-   実行可能ファイルを作成する前に、「[方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)」で説明されている手順に従って、**プロジェクト デザイナー**で定数を設定します。|  
  
||  
|-|  
|コマンド ラインで定数を設定するには|  
|-   次のように、**\/d** スイッチを使って条件付きコンパイル定数を入力します。<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     **\/d** スイッチと最初の定数の間にスペースは必要ありません。  詳細については、「[\/define](../../../visual-basic/reference/command-line-compiler/define.md)」を参照してください。<br />     コマンド ラインで設定する定数の値は**プロジェクト デザイナー**で行った設定より優先されますが、プロジェクト デザイナーで行った設定は消去されません。  **プロジェクト デザイナー**で行った引数の設定は、以降のコンパイルでも有効です。<br />     コード自体に定数を記述する場合は、定数の宣言を行ったモジュール全体が定数のスコープになるため、配置場所に関する厳密な規則はありません。|  
  
||  
|-|  
|コード内で定数を設定するには|  
|-   定数を使用するモジュールの宣言ブロックに定数を配置します。  このように配置すると、コードが整理されてわかりやすくなります。|  
  
## 関連トピック  
  
|||  
|-|-|  
|Title|Description|  
|[プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|読みやすく管理しやすいコードを作成するためのヒントを紹介します。|  
  
## Reference  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)