---
title: "Visual Basic プログラムの構造 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- conditional compilation, Visual Basic
- program structure, Visual Basic
- procedures, structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 64aab045538461d86946c870fa428bf8ad4ec15e
ms.lasthandoff: 03/13/2017

---
# <a name="structure-of-a-visual-basic-program"></a>Visual Basic プログラムの構造
A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムは、標準の構成ブロックから構築します。 A*ソリューション*1 つまたは複数のプロジェクトで構成されます。 A*プロジェクト*さらに、1 つまたは複数のアセンブリを含めることができます。 各*アセンブリ*が&1; つまたは複数のソース ファイルからコンパイルします。 A*ソースファイル*定義とクラス、構造体、モジュール、および最終的には、すべてのコードが含まれているインターフェイスの実装を提供します。  
  
 これらの構成要素の詳細については、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムを参照してください[ソリューションとプロジェクト](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio)と[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)します。  
  
## <a name="file-level-programming-elements"></a>ファイル レベルのプログラミング要素  
 プロジェクトまたはファイルを起動して、コード エディターを開いた場所に既に存在し、正しい順序でいくつかのコードが表示されます。 作成するすべてのコードは、次の順序に従う必要があります。  
  
1.  `Option`ステートメント  
  
2.  `Imports`ステートメント  
  
3.  `Namespace`ステートメントと名前空間レベル要素  
  
 別の順序でステートメントを入力すると、コンパイル エラーが発生することができます。  
  
 プログラムでは、条件付きコンパイル ステートメントを含めることもできます。 上記の一連のステートメントの間でソース ファイルを挿入することができます。  
  
### <a name="option-statements"></a>オプション ステートメント  
 `Option`ステートメントは、後続のコードでは、構文とロジックのエラーを防ぐの基盤となる規則を確立します。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)により、すべての変数が宣言されのスペルが正しいデバッグ時間が削減されます。 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)を異なるデータ型の変数を使用するときに発生するロジック エラーやデータ損失を最小限に抑えることができます。 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)方法文字列は、互いにいずれかに基づく比較を示す、`Binary`または`Text`値。  
  
### <a name="imports-statements"></a>Imports ステートメント  
 含めることができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)プロジェクトの外部で定義されている名前をインポートします。 `Imports`ステートメントでは、クラスとその他の型を修飾しなくても、インポートされた名前空間内で定義を参照するようにコードを使用できます。 できるだけ使用することができます`Imports`ステートメントに該当します。 詳細については、次を参照してください。[参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)します。  
  
### <a name="namespace-statements"></a>Namespace ステートメント  
 名前空間のヘルプの編成し、分類、プログラミングの要素をグループ化およびへのアクセスを簡素化できます。 使用する、 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)を特定の名前空間内で次のステートメントを分類します。 詳細については、次を参照してください。 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)します。  
  
### <a name="conditional-compilation-statements"></a>条件付きコンパイル ステートメント  
 条件付きコンパイル ステートメントは、ソース ファイルにどこに表示できます。 含まれているまたは特定の条件によってコンパイル時に除外するコードの部分と、されます。 行えますに、アプリケーションのデバッグに条件付きコードがデバッグ モードのみで実行されているためです。 詳細については、次を参照してください。[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)します。  
  
## <a name="namespace-level-programming-elements"></a>Namespace レベルのプログラミング要素  
 クラス、構造体、およびモジュールには、ソース ファイル内のすべてのコードが含まれます。 *名前空間レベル*要素、またはソース ファイル レベルでは、名前空間内で表示することができます。 その他のすべてのプログラミング要素の宣言を保持します。 要素のシグネチャを定義しますが、実装を提供しない、インターフェイスは、モジュール レベルも表示されます。 モジュール レベルの要素の詳細については、次を参照してください。  
  
-   [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 名前空間レベルでのデータ要素は、列挙体およびデリゲートです。  
  
## <a name="module-level-programming-elements"></a>モジュール レベルのプログラミング要素  
 プロシージャ、演算子、プロパティ、およびイベントは、実行可能コード (実行時にアクションを実行するステートメント) が保持できる唯一のプログラミング要素です。 *モジュール レベル*プログラムの要素。 プロシージャ レベル要素の詳細については、次を参照してください。  
  
-   [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 モジュール レベルのデータ要素は、変数、定数、列挙型、およびデリゲート。  
  
## <a name="procedure-level-programming-elements"></a>プロシージャ レベルのプログラミング要素  
 内容のほとんど*プロシージャ レベル*要素は、実行可能ステートメントは、プログラムの実行時のコードを構成します。 すべての実行可能コードがいくつかの手順である必要があります (`Function`、 `Sub`、 `Operator`、 `Get`、 `Set`、 `AddHandler`、 `RemoveHandler`、 `RaiseEvent`)。 詳細については、次を参照してください。[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)します。  
  
 プロシージャ レベルでのデータ要素は、ローカル変数および定数に限定されます。  
  
## <a name="the-main-procedure"></a>メインのプロシージャ  
 `Main`プロシージャは、アプリケーションが読み込まれているときに実行する最初のコードです。 `Main`開始点し、アプリケーション全体を制御します。 次の&4; 種類がある`Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 この手順の最も一般的なさまざまなの`Sub Main()`です。 詳細については、次を参照してください。 [Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)   
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Visual Basic の制限事項](../../../visual-basic/programming-guide/program-structure/limitations.md)
