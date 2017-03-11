---
title: "Structure of a Visual Basic Program | Microsoft Docs"
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
  - "conditional compilation, Visual Basic"
  - "program structure, Visual Basic"
  - "procedures, structure"
  - "Visual Basic code, program structure"
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Structure of a Visual Basic Program
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プログラムは、標準ビルド ブロックから構築されます。  *ソリューション*は、1 つ以上のプロジェクトで構成されます。  *プロジェクト*は、1 つ以上のアセンブリで構成されます。  各*アセンブリ*は、1 つ以上のソース ファイルからコンパイルされます。  *ソース ファイル*は、クラス、構造体、モジュール、およびインターフェイスの定義と実装を提供します。すべてのコードがここに含まれます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プログラムのこれらのビルド ブロックの詳細については、「[ソリューションおよびプロジェクト](/visual-studio/ide/solutions-and-projects-in-visual-studio)」および「[アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## ファイル レベルのプログラミング要素  
 プロジェクトまたはファイルを開始してコード エディターを開くと、一部のコードが既に適切な順序で配置されて表示されます。  作成するコードはすべて以下の順序に従う必要があります。  
  
1.  `Option` ステートメント  
  
2.  `Imports` ステートメント  
  
3.  `Namespace` ステートメントおよび名前空間レベルの要素  
  
 ステートメントをこれとは別の順序で入力すると、コンパイル エラーが発生することがあります。  
  
 プログラムには、条件付きコンパイル ステートメントを指定することもできます。  このようなステートメントは、ソース ファイル内で上記の順序で記述するステートメントの中に混在できます。  
  
### Option ステートメント  
 `Option` ステートメントは後続のコードの基本的な規則を確立し、構文エラーや論理エラーの発生を防ぎます。  [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) は、すべての変数が正しく宣言され、スペルに誤りがないことを保証するので、デバッグ時間が短縮されます。  [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) ステートメントは、異なる型の変数を使用するときに起こり得るデータの損失や論理エラーを減らすために役立ちます。  [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) には、`Binary` 値または `Text` 値に基づいて文字列を比較する方法を指定します。  
  
### Imports ステートメント  
 プロジェクトの外部で定義された名前をインポートするために、[Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) を指定できます。  `Imports` ステートメントを使うと、インポートした名前空間に定義されているクラスおよびその他の型を修飾なしで参照できます。  `Imports` ステートメントは必要に応じていくつでも使用できます。  詳細については、「[References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)」を参照してください。  
  
### Namespace ステートメント  
 名前空間は、プログラミング要素を整理および分類してグループ分けやアクセスをしやすくするために役立ちます。  [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) を使って、以下に示すステートメントを特定の名前空間に分類できます。  詳細については、「[Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)」を参照してください。  
  
### 条件付きコンパイル ステートメント  
 条件付きコンパイル ステートメントは、ソース ファイル内のほとんどの場所で使用できます。  特定の条件に基づいて、コードの一部をコンパイル時に含めることや除外することができます。  条件付きコードはデバッグ モードだけで実行されるため、条件付きコンパイル ステートメントはアプリケーションのデバッグにも使用できます。  詳細については、「[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)」を参照してください。  
  
## 名前空間レベルのプログラミング要素  
 クラス、構造体、およびモジュールのすべてのコードはソース ファイルに含まれます。  これらは*名前空間レベル*の要素であり、名前空間またはソース ファイルのレベルで指定できます。  これらの要素には、他のすべてのプログラミング要素の宣言が格納されます。  要素のシグネチャを定義するだけで実装を提供しないインターフェイスも、モジュール レベルで指定します。  モジュール レベルの各要素の詳細については、次のトピックを参照してください。  
  
-   [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 名前空間レベルのデータ要素は、列挙およびデリゲートです。  
  
## モジュール レベルのプログラミング要素  
 プロシージャ、演算子、プロパティ、およびイベントだけが、実行可能コード \(実行時にアクションを実行するステートメント\) を含むことができるプログラミング要素です。  これらは、プログラムの*モジュール レベル*の要素です。  プロシージャ レベルの各要素の詳細については、次のトピックを参照してください。  
  
-   [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 モジュール レベルのデータ要素は、変数、定数、列挙、およびデリゲートです。  
  
## プロシージャ レベルのプログラミング要素  
 ほとんどの*プロシージャ レベル*要素の内容は、実行可能なステートメントであり、プログラム コードの一部を構成します。  すべての実行可能コードは、プロシージャ \(`Function`、`Sub`、`Operator`、`Get`、`Set`、`AddHandler`、`RemoveHandler`、`RaiseEvent`\) に含める必要があります。  詳細については、「[Statements](../../../visual-basic/programming-guide/language-features/statements.md)」を参照してください。  
  
 プロシージャ レベルのデータ要素は、ローカル変数とローカル定数だけです。  
  
## Main プロシージャ  
 `Main` プロシージャは、アプリケーションが読み込まれた後で最初に実行されるコードです。  `Main` はアプリケーションの開始点であり、アプリケーション全体を制御します。  `Main` には次の 4 種類があります。  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 最も一般的に使用されるプロシージャは、`Sub Main()` です。  詳細については、「[Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)」を参照してください。  
  
## 参照  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/ja-jp/9d030b60-e148-4366-a462-69532f02294c)   
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)