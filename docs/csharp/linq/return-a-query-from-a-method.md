---
title: "メソッドからクエリを返す"
description: "クエリを返す方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 747345f0a765bc6cbe947a2b0c7bc025eb599550
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>方法 : メソッドからクエリを返す (C# プログラミング ガイド)
この例では、メソッドから、クエリを戻り値として返す方法と `out` パラメーターとして返す方法を示します。  
  
 クエリ オブジェクトはコンポーザブルです。つまり、メソッドからクエリを返すことができます。 クエリを表すオブジェクトには、結果のコレクションではなく、必要に応じて結果を生成する手順が格納されます。 メソッドからクエリ オブジェクトを返すメリットは、そのオブジェクトをさらに構成したり変更したりできることです。 そのため、クエリを返すメソッドの戻り値または `out` パラメーターも同じ型である必要があります。 メソッドがクエリを具象型 <xref:System.Collections.Generic.List%601> または <xref:System.Array> に実体化する場合は、そのメソッドは、クエリ自体ではなくクエリ結果を返すと見なされます。 メソッドから返されたクエリ変数は、引き続き構成または変更できます。  
  
## <a name="example"></a>例  
 次の例は、最初のメソッドはクエリを戻り値として返し、2 番目のメソッドはクエリを `out` パラメーターとして返しています。 どちらの場合も返されるのはクエリであり、クエリ結果ではないことに注意してください。  
  
 [!code-cs[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)

