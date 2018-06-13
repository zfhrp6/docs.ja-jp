---
title: Visual Basic プログラムの構造
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5c45cc8982a03d5bdd974434164187b03529ae05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654831"
---
# <a name="structure-of-a-visual-basic-program"></a>Visual Basic プログラムの構造
Visual Basic プログラムは、標準の構成ブロックから構築します。 A*ソリューション*1 つまたは複数のプロジェクトで構成されます。 A*プロジェクト*さらに、1 つまたは複数のアセンブリを含めることができます。 各*アセンブリ*が 1 つまたは複数のソース ファイルからコンパイルします。 A*ソースファイル*定義とクラス、構造体、モジュール、および最終的にすべてのコードが含まれているインターフェイスの実装を提供します。  
  
 Visual Basic プログラムの詳細については、これらの構成要素は、次を参照してください。[ソリューションとプロジェクト](/visualstudio/ide/solutions-and-projects-in-visual-studio)と[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)です。  
  
## <a name="file-level-programming-elements"></a>ファイル レベルのプログラミング要素  
 プロジェクトまたはファイルを開始する、コード エディターを開くと、既に実行されていると、正しい順序でいくつかのコードを参照してください。 すべてのコードを記述するは、次の順序に従う必要があります。  
  
1.  `Option` ステートメント  
  
2.  `Imports` ステートメント  
  
3.  `Namespace` ステートメントと名前空間レベル要素  
  
 異なる順序でステートメントを入力すると、コンパイル エラーが発生することができます。  
  
 プログラムは、条件付きコンパイル ステートメントを含めることもできます。 上記の一連のステートメントの間でソース ファイルでこれらを挿入することができます。  
  
### <a name="option-statements"></a>ステートメントのオプション  
 `Option` ステートメントは、構文とロジック エラーを回避することができ、後続のコードの基本的な規則を確立します。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)いるすべての変数の宣言し、の綴り、デバッグ時間を短縮することを確認します。 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)を異なるデータ型の変数間で作業するときに発生する可能性がロジックのエラーやデータの損失を最小限に抑えるのに役立ちます。 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)方法文字列は、互いにいずれかに基づく比較を指定します、`Binary`または`Text`値。  
  
### <a name="imports-statements"></a>Imports ステートメント  
 含めることができます、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)名、プロジェクトの外側で定義をインポートします。 `Imports`ステートメントにより、コードをクラスとそれらを修飾することがなく、インポートされた名前空間内で定義されているその他の型を参照してください。 できるだけ使用することができます`Imports`に応じてステートメントです。 詳細については、次を参照してください。[参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)です。  
  
### <a name="namespace-statements"></a>Namespace ステートメント  
 名前空間のヘルプ整理して、グループ化とへのアクセスの容易にするためのプログラミング要素を分類します。 使用する、 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)を特定の名前空間内で次のステートメントを分類します。 詳細については、「[Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)」を参照してください。  
  
### <a name="conditional-compilation-statements"></a>条件付きコンパイル ステートメント  
 条件付きコンパイル ステートメントは、ソース ファイルでほぼどこでも表示できます。 含まれているまたは特定の条件によってコンパイル時に除外するコードの部分と、されます。 使用することも、アプリケーションのデバッグの条件付きコードがデバッグ モードのみで実行されるためです。 詳細については、次を参照してください。[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)です。  
  
## <a name="namespace-level-programming-elements"></a>Namespace レベルのプログラミング要素  
 クラス、構造体、およびモジュールには、ソース ファイル内のすべてのコードが含まれています。 *名前空間レベル*要素、またはファイル レベルのソースを名前空間内に表示されることができます。 その他のすべてのプログラミング要素の宣言が格納されます。 要素のシグネチャを定義しますが、実装を提供しない、インターフェイスは、モジュール レベルも表示されます。 モジュール レベルの要素の詳細については、次を参照してください。  
  
-   [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 名前空間レベルでのデータ要素は、列挙およびデリゲートです。  
  
## <a name="module-level-programming-elements"></a>モジュール レベルのプログラミング要素  
 プロシージャ、演算子、プロパティ、およびイベントは、実行可能コード (実行時にアクションを実行するステートメント) が保持できる唯一のプログラミング要素です。 *モジュール レベル*プログラムの要素。 プロシージャ レベルの要素の詳細については、次を参照してください。  
  
-   [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 モジュール レベルのデータ要素は、変数、定数、列挙型、およびデリゲートされます。  
  
## <a name="procedure-level-programming-elements"></a>プロシージャ レベルのプログラミング要素  
 ほとんどの内容の*プロシージャ レベル*要素は、実行可能なステートメントは、プログラムの実行時のコードを構成します。 すべての実行可能コードは、いくつかの手順である必要があります (`Function`、 `Sub`、 `Operator`、 `Get`、 `Set`、 `AddHandler`、 `RemoveHandler`、 `RaiseEvent`)。 詳細については、「[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)」を参照してください。  
  
 プロシージャ レベルのデータ要素は、ローカル変数および定数に限定されます。  
  
## <a name="the-main-procedure"></a>Main プロシージャ  
 `Main`プロシージャは、アプリケーションが読み込まれているときに実行する最初のコード。 `Main` 開始ポイントとアプリケーションの全体的なコントロールとして機能します。 次の 4 種類がある`Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 この手順の最も一般的なさまざまな`Sub Main()`します。 詳細については、次を参照してください。 [Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Visual Basic の制限事項](../../../visual-basic/programming-guide/program-structure/limitations.md)
