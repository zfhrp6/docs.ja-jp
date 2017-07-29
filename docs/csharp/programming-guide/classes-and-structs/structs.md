---
title: "構造体 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: 31
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ce12f402c0748ea6729c82e3f188c0a58f63d628
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="structs-c-programming-guide"></a>構造体 (C# プログラミング ガイド)
構造体は [struct](../../../csharp/language-reference/keywords/struct.md) キーワードを使って定義します。次はその例です。  
  
 [!code-cs[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 構造体は、構文上はクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。  
  
-   構造体宣言内では、const または static と宣言されているフィールド以外は初期化できません。  
  
-   構造体では、既定のコンストラクター (パラメーターなしのコンストラクター) やファイナライザーを宣言できません。  
  
-   構造体は、割り当て時にコピーされます。 構造体を新しい変数に割り当てると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。 これは、Dictionary\<string, myStruct> などの値の型のコレクションを使用する際に重要です。  
  
-   構造体は値型ですが、クラスは参照型です。  
  
-   クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。  
  
-   構造体は、パラメーターのあるコンストラクターを宣言できます。  
  
-   構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。 すべての構造体が `System.ValueType` を直接継承し、System.ValueType は `System.Object` を継承します。  
  
-   構造体は、インターフェイスを実装できます。  
  
-   構造体は、null 許容型として使うことができ、null 値を割り当てることができます。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [方法: メソッドに構造体を渡すこととクラス参照を渡すことの違いを理解する](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)

