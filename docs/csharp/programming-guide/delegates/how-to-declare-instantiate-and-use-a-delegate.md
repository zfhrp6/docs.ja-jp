---
title: "方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5a5329b9e99fcd5830a57eb8f97b4edb67ad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)
C# 1.0 以降では、次の例に示すようにデリゲートを宣言できます。  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# 2.0 では、次の例に示すように、上記の宣言をより簡単に記述できます。  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 C# 2.0 以降では、次の例に示すように、匿名メソッドを使用して[デリゲート](../../../csharp/language-reference/keywords/delegate.md)の宣言と初期化を行うこともできます。  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 C# 3.0 以降では、次の例に示すように、ラムダ式を使用してデリゲートの宣言とインスタンス化を行うこともできます。  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 詳しくは、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」をご覧ください。  
  
 次の例で、デリゲートの宣言、インスタンス化、および使用の方法について説明します。 `BookDB` クラスにより、書籍のデータベースを保持する書店データベースをカプセル化します。 これは、データベース内にあるすべてのペーパーバックを検索し、各ペーパーバックに対してデリゲートを呼び出す `ProcessPaperbackBooks` メソッドを公開します。 使用する `delegate` 型には `ProcessBookDelegate` という名前を付けます。 `Test` クラスでは、このクラスを使用してペーパーバックのタイトルと平均価格を出力します。  
  
 デリゲートを使用することで、書店データベースとクライアント コードの機能を適切に分離しやすくなります。 クライアント コードからは、書籍の格納方法や書店コードでのペーパーバックの検索方法はわかりません。 書店コードからは、検索後にペーパーバックに対して行われる処理はわかりません。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
-   デリゲートを宣言する。  
  
     次のステートメントで、新しいデリゲート型を宣言します。  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     各デリゲート型は、引数の数と型、およびデリゲートでカプセル化可能なメソッドの戻り値の型を示します。 引数型または戻り値型のセットが新しく必要になった場合は、常に新しいデリゲート型を宣言する必要があります。  
  
-   デリゲートをインスタンス化する。  
  
     デリゲート型の宣言後、デリゲート オブジェクトを作成して特定のメソッドに関連付ける必要があります。 先の例では、次の例に示すように `PrintTitle` メソッドを `ProcessPaperbackBooks` メソッドに渡すことでこの操作を行っています。  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     これにより、[静的](../../../csharp/language-reference/keywords/static.md) メソッド `Test.PrintTitle` に関連付けられた新しいデリゲート オブジェクトが作成されます。 同様に、次の例で示すようにオブジェクト `totaller` の非静的メソッド `AddBookToTotal` も渡しています。  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     どちらの場合でも、新しいデリゲート オブジェクトが `ProcessPaperbackBooks` メソッドに渡されます。  
  
     デリゲート オブジェクトは不変であるため、関連付けられているメソッドを、デリゲートの作成後に変更することはできません。  
  
-   デリゲートを呼び出す。  
  
     デリゲート オブジェクトを作成したら、通常は、そのデリゲートを呼び出す別のコードにデリゲート オブジェクトを渡します。 デリゲート オブジェクトを呼び出すときには、デリゲートに渡す引数を、デリゲート オブジェクト名の後ろにかっこで囲んで付けます。 デリゲートの呼び出しの例を次に示します。  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     デリゲートは、この例に示すように同期的に呼び出すことも、`BeginInvoke` メソッドおよび `EndInvoke` メソッドを使用して非同期的に呼び出すこともできます。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [イベント](../../../csharp/programming-guide/events/index.md)  
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)
