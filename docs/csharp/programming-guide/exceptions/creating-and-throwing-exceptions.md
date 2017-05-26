---
title: "例外の作成とスロー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c3eab50a6a785676dd397498fbe95348187e2b7e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>例外の作成とスロー (C# プログラミング ガイド)
例外は、プログラムの実行中にエラーが発生したことを示すために使われます。 エラーを説明する例外オブジェクトが作成された後、[throw](../../../csharp/language-reference/keywords/throw.md) キーワードで "*スロー*" されます。 そのとき、ランタイムは最も互換性のある例外ハンドラーを検索します。  
  
 プログラマは、以下の条件が 1 つでも該当するときは、例外をスローする必要があります。  
  
-   メソッドは、定義されている機能を完了できません。  
  
     たとえば、メソッドへのパラメーターに無効な値が設定されている場合などです。  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   オブジェクトの状態に基づくと、オブジェクトに対して行われた呼び出しが不適切です。  
  
     たとえば、読み取り専用ファイルに書き込もうとしたような場合です。 オブジェクトの状態により操作が許可されない場合は、<xref:System.InvalidOperationException> のインスタンスまたはこのクラスの派生に基づくオブジェクトをスローします。 次に示すのは、<xref:System.InvalidOperationException> オブジェクトをスローするメソッドの例です。  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   メソッドへの引数が原因で例外が発生しました。  
  
     この場合は、元の例外をキャッチして、<xref:System.ArgumentException> のインスタンスを作成する必要があります。 元の例外は、<xref:System.ArgumentException> のコンストラクターに <xref:System.Exception.InnerException%2A> パラメーターとして渡す必要があります。  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 例外には、<xref:System.Exception.StackTrace%2A> という名前のプロパティが含まれています。 この文字列には、現在の呼び出し履歴でのメソッドの名前と、各メソッドの例外がスローされたファイル名と行番号が含まれます。 スタック トレースを開始するポイントから例外をスローする必要があるため、共通言語ランタイム (CLR) によって `throw` ステートメントのポイントから <xref:System.Exception.StackTrace%2A> オブジェクトが自動的に作成されます。  
  
 すべての例外には、<xref:System.Exception.Message%2A> という名前のプロパティが含まれます。 例外の原因を説明するには、この文字列を設定する必要があります。 機密性の高い情報はメッセージ テキストに入れないようにする必要があることに注意してください。 <xref:System.Exception.Message%2A> に加えて、<xref:System.ArgumentException> には <xref:System.ArgumentException.ParamName%2A> という名前のプロパティが含まれ、これには例外がスローされる原因になった引数の名前を設定する必要があります。 プロパティ セッターの場合、<xref:System.ArgumentException.ParamName%2A> には `value` を設定する必要があります。  
  
 パブリックのプロテクト メソッド メンバーは、意図された機能を完了できない場合は常に例外をスローする必要があります。 スローされる例外クラスは、エラー状態に適合する使用可能な例外の中で最も具体的なものである必要があります。 これらの例外はクラスの機能の一部として文書化する必要があり、派生クラスまたは元のクラスの更新では、旧バージョンとの互換性のために同じ動作を維持する必要があります。  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>例外をスローするときに避ける必要があること  
 次の一覧は、例外をスローするときに避ける必要があることです。  
  
-   通常の実行の一部として、例外を使ってプログラムのフローを変更しないでください。 例外は、エラー状態の報告と処理のためだけに使う必要があります。  
  
-   スローする代わりに、戻り値またはパラメーターとして例外を返さないでください。  
  
-   ユーザー作成のソース コードからは、<xref:System.Exception?displayProperty=fullName>、<xref:System.SystemException?displayProperty=fullName>、<xref:System.NullReferenceException?displayProperty=fullName>、または <xref:System.IndexOutOfRangeException?displayProperty=fullName> を意図的にスローしないでください。  
  
-   デバッグ モードではスローでき、リリース モードではスローできない例外は、作成しないでください。 開発フェーズ中に実行時エラーを識別するには、代わりにデバッグ アサートを使ってください。  
  
## <a name="defining-exception-classes"></a>例外クラスの定義  
 プログラムでは、<xref:System> 名前空間で事前定義された例外クラスをスローするか (上記の場合を除きます)、<xref:System.Exception> から派生することで独自の例外クラスを作成することができます。 派生クラスでは、少なくとも 4 つのコンストラクターを定義する必要があります。既定のコンストラクター、メッセージ プロパティを設定するコンストラクター、<xref:System.Exception.Message%2A> プロパティと <xref:System.Exception.InnerException%2A> プロパティの両方を設定するコンストラクター、 そして 4 番目は例外のシリアル化に使われるコンストラクターです。 新しい例外クラスは、シリアル化可能にする必要があります。 例:  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 例外クラスへの新しいプロパティの追加は、プロパティによって提供されるデータが例外の解決に役立つ場合にのみ行う必要があります。 派生例外クラスに新しいプロパティを追加する場合は、`ToString()` をオーバーライドして追加情報を返す必要があります。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)   
 [例外階層](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)
