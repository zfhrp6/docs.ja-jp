---
title: ".NET での新しい文字列を作成します。"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a>.NET での新しい文字列を作成します。
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]により、単純な代入を使用して作成される文字列とも異なるパラメーターの番号を使用して文字列の作成をサポートするクラスのコンス トラクター オーバー ロードします。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]もいくつかのメソッドを提供、<xref:System.String?displayProperty=nameWithType>新しい文字列を作成するクラスがいくつかの文字列、文字列の配列を組み合わせることによってオブジェクトまたはオブジェクトします。  
  
## <a name="creating-strings-using-assignment"></a>割り当てを使用した文字列の作成  
 新しいを作成する最も簡単な方法<xref:System.String>オブジェクトを単に文字列リテラルを代入する<xref:System.String>オブジェクト。  
  
## <a name="creating-strings-using-a-class-constructor"></a>クラス コンストラクターを使用した文字列の作成  
 オーバー ロードを使用することができます、<xref:System.String>クラス コンス トラクターを文字配列から文字列を作成します。 また、指定した回数だけ特定の文字を複製することで、新しい文字列を作成することもできます。  
  
## <a name="methods-that-return-strings"></a>文字列を返すメソッド  
 次の表は、新しい文字列オブジェクトを返すいくつかの便利なメソッドを示しています。  
  
|メソッド名|用途|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|入力オブジェクトのセットから、書式設定された文字列をビルドします。|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|2 つ以上の文字列から文字列をビルドします。|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|文字列の配列を組み合わせることで、新しい文字列をビルドします。|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|既存の文字列の指定のインデックスに文字列を挿入することで、新しい文字列をビルドします。|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|文字配列内の指定の位置に、文字列内の指定の文字をコピーします。|  
  
### <a name="format"></a>形式  
 使用することができます、 **String.Format**複数のオブジェクトを表す文字列を書式設定された文字列を作成し、連結します。 このメソッドは、渡されたすべてのオブジェクトを文字列に自動的に変換します。 たとえば、アプリケーションを表示する必要があります、 **Int32**値と**DateTime**値、ユーザーを使用してこれらの値を表す文字列を簡単に作成できる、**形式**メソッドです。 このメソッドで使用される書式設定規則については、[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)に関するセクションを参照してください。  
  
 次の例では、**形式**整数変数を使用する文字列を作成します。  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 この例では<xref:System.DateTime.Now%2A?displayProperty=nameWithType>現在のスレッドに関連付けられているカルチャで指定された方法で現在の日付と時刻を表示します。  
  
### <a name="concat"></a>Concat  
 **String.Concat**を簡単に 2 つ以上の既存のオブジェクトから、新しい文字列オブジェクトを作成するメソッドを使用できます。 言語に依存せずに文字列を連結する方法を提供します。 このメソッドから派生した任意のクラスを受け入れる**System.Object**です。 次の例では、2 つの既存の文字列オブジェクトおよび区切り文字から文字列を作成します。  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 **先**メソッドは、文字列と区切り記号文字列の配列から新しい文字列を作成します。 このメソッドは、複数の文字列を連結して、たとえばコンマで区切られたリストを作成する場合に便利です。  
  
 次の例では、スペースを使用して文字列の配列をバインドします。  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>挿入  
 **String.Insert**メソッドは、文字列を別の文字列内の指定位置に挿入すると、新しい文字列を作成します。 このメソッドは、0 から始まるインデックスを使用します。 次の例では、`MyString` の 5 番目のインデックス位置に文字列を挿入し、この値を持つ新しい文字列を作成します。  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo**メソッドは、文字列の一部分を文字の配列にコピーします。 文字列の開始インデックスと、コピーする文字数の両方を指定できます。 このメソッドは、ソース インデックス、文字配列、コピー先のインデックス、およびコピーする文字数を受け取ります。 すべてのインデックスは 0 から始まります。  
  
 次の例では、 **CopyTo**にオブジェクトの文字列「こんにちは」という語の文字を文字の配列の最初のインデックス位置にコピーする方法です。  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>関連項目  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)  
 [複合書式指定](../../../docs/standard/base-types/composite-formatting.md)
