---
title: "ジェネリック (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: de81058173b0985577474e8601aa84d4e83336a5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="generics-c-programming-guide"></a>ジェネリック (C# プログラミング ガイド)
ジェネリックは、バージョン 2.0 の C# 言語と共通言語ランタイム (CLR) に追加されたものです。 ジェネリックは、.NET Framework に型パラメーターという概念を導入します。型パラメーターを使用すると、クラスやメソッドがクライアント コードで宣言され、インスタンス化されるまで、1 つ以上の型の指定を遅延させるクラスとメソッドを設計できます。 たとえば、ジェネリック型パラメーター T を使用すると、次に示すようにランタイムのキャストやボックス化操作のコストやリスクを負わずに他のクライアント コードで使用できる単一のクラスを記述できます。  
  
 [!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>ジェネリックの概要  
  
-   ジェネリック型は、コードの再利用、タイプ セーフ、およびパフォーマンスを最大化するために使用します。  
  
-   ジェネリックの最も一般的な用途は、コレクション クラスの作成です。  
  
-   .NET Framework クラス ライブラリには、複数の新しいジェネリック コレクション クラスが <xref:System.Collections.Generic> 名前空間に含まれています。 <xref:System.Collections> 名前空間の <xref:System.Collections.ArrayList> などのクラスの代わりとして、できる限りこれらを使用してください。  
  
-   独自のジェネリック インターフェイス、クラス、メソッド、イベントおよびデリゲートを作成することができます。  
  
-   ジェネリック クラスは、特定のデータ型のメソッドへのアクセスを有効にするように制限できます。  
  
-   ジェネリック データ型で使用される型に関する情報は、実行時にリフレクションを使用して取得できます。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [ジェネリックの利点](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [ジェネリック型パラメーター](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [ジェネリック インターフェイス](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [C++ テンプレートと C# ジェネリックの違い](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [.NET Framework クラス ライブラリのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 詳細については、「[C# 言語の仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)   
 [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

