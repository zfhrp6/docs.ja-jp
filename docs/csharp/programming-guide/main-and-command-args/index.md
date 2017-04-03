---
title: "Main() とコマンド ライン引数 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f6934a09c5f980f845e19b28e462cc601e154512
ms.lasthandoff: 03/13/2017

---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() とコマンド ライン引数 (C# プログラミング ガイド)
`Main` メソッドは、C# コンソール アプリケーションまたは Windows アプリケーションのエントリ ポイントです (ライブラリおよびサービスでは、エントリ ポイントとしての `Main` メソッドは必要ありません)。 アプリケーションを起動すると、最初に `Main` メソッドが呼び出されます。  
  
 C# プログラムのエントリ ポイントは 1 つのみです。 `Main` メソッドを持つクラスが 2 つ以上ある場合、プログラムをコンパイルする際に **/main** コンパイラ オプションを使用して、どの `Main` メソッドをエントリ ポイントとして使用するかを指定する必要があります。 詳細については、「[/main (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)」を参照してください。  
  
 [!code-cs[csProgGuideMain 17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]  
  
## <a name="overview"></a>概要  
  
-   `Main` メソッドは .exe プログラムのエントリ ポイントです。ここで、プログラムの制御を開始および終了します。  
  
-   `Main` は、クラスまたは構造体の内部で宣言されます。 `Main` は [public](../../../csharp/language-reference/keywords/public.md) ではなく、[static](../../../csharp/language-reference/keywords/static.md) である必要があります (先ほどの例では、既定の [private](../../../csharp/language-reference/keywords/private.md) のアクセスを受け取ります)。外側のクラスまたは構造体は、static である必要はありません。  
  
-   `Main` の戻り値は、`void` または `int` のいずれかになります。  
  
-   `Main` メソッドを宣言する際、コマンドライン引数を含む `string[]` パラメーターは指定してもしなくてもかまいません。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] を使用して Windows フォーム アプリケーションを作成する場合、パラメーターを手動で追加するか、<xref:System.Environment> クラスを使用してコマンドライン引数を取得します。 パラメーターは、インデックス 0 のコマンドライン引数として読み取られます。 C や C++ とは異なり、プログラムの名前が最初のコマンドライン引数として扱われることはありません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [コマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Main() の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [インサイド C# プログラム](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<paveover>C# サンプル アプリケーション](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)
