---
title: Visual Basic での条件付きコンパイル
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 496df36242c6b43e7e3ec94ce675d11177e8b466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653018"
---
# <a name="conditional-compilation-in-visual-basic"></a>Visual Basic での条件付きコンパイル
*条件付きコンパイル*、他のユーザーは無視されます、特定のプログラムではコード ブロックは選択的にコンパイルします。  
  
 たとえば、書き込むする可能性があるか、同じプログラミング タスクを別のアプローチの速度を比較するステートメントをデバッグすることが複数言語のアプリケーションをローカライズします。 条件付きコンパイル ステートメントは実行時ではなく、コンパイル時に実行するよう設計されています。  
  
 条件付きでコンパイルされているコードのブロックを指定、`#If...Then...#Else`ディレクティブです。 たとえば、フランス語、ドイツ語を作成する同じから同じアプリケーションのバージョンのソース コード、プラットフォーム固有のコードのセグメントを埋め込む`#If...Then`定義済みの定数を使用して、ステートメント`FrenchVersion`と`GermanVersion`です。 次の例でどのようにします。  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 値を設定した場合、`FrenchVersion`に条件付きコンパイル定数`True`コンパイル時に、フランス語版の条件付きのコードがコンパイルされています。 値を設定した場合、`GermanVersion`に定数`True`コンパイラがドイツ語版を使用します。 どちらに設定されている場合`True`、最後にコード`Else`ブロックが実行されます。  
  
> [!NOTE]
>  オートコンプリートは、コードの編集時に機能しないと、コードが現在のブランチの一部ではない場合は、条件付きコンパイル ディレクティブを使用するには。  
  
## <a name="declaring-conditional-compilation-constants"></a>条件付きコンパイル定数を宣言します。  
 3 つの方法のいずれかで条件付きコンパイル定数を設定できます。  
  
-   **プロジェクト デザイナー**  
  
-   コマンド ライン コンパイラを使用するときに、コマンドラインで  
  
-   コードで  
  
 条件付きコンパイル定数は、特殊なスコープを持ち、標準的なコードからアクセスできません。 条件付きコンパイル定数のスコープは、設定されている方法によって異なります。 次の表は、上記で説明した 3 つの方法のそれぞれを使用して宣言されている定数のスコープを一覧表示します。  
  
|定数を設定する方法|定数のスコープ|  
|---|---|  
|**プロジェクト デザイナー**|プロジェクト内のすべてのファイルへの公開|  
|コマンド ライン|コマンド ライン コンパイラに渡されるすべてのファイルへの公開|  
|`#Const` コード内のステートメント|プライベートに宣言されているファイル|  
  
|プロジェクト デザイナーで定数を設定するには|  
|---|  
|実行可能ファイルを作成する前定数を設定、**プロジェクト デザイナー**で提供される手順に従って、[管理プロジェクトおよびソリューションのプロパティ](/visualstudio/ide/managing-project-and-solution-properties)です。|  
  
|コマンドラインで定数を設定するには|  
|---|  
|-を使用して、 **/d**スイッチを次の例のように、条件付きコンパイル定数を入力します。<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     間で必要な空き領域がない、 **/d**スイッチとの最初の定数です。 詳細については、次を参照してください。 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)です。<br />     コマンド ラインの宣言で入力した宣言のオーバーライド、**プロジェクト デザイナー**は消去されません。 引数の設定**プロジェクト デザイナー**後続のコンパイルを有効になります。<br />     定数をそれ自体のコードを記述する場合はありません、配置に関する厳密な規則のスコープが宣言されているモジュール全体であるため。|  
  
|コード内の定数を設定するには|  
|---|  
|-定数を使用するモジュールの宣言ブロックに配置します。 これにより、整理したり読みやすく、コードを維持します。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|---|---|  
|[プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|コードを容易に読み取りおよびメンテナンスについて説明します。|  
  
## <a name="reference"></a>参照  
 [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
