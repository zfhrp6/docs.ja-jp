---
title: "フィールド (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
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
ms.openlocfilehash: 1e5b1880e6821b2fd4595baad31f7a1bd5599ac4
ms.lasthandoff: 03/13/2017

---
# <a name="fields-c-programming-guide"></a>フィールド (C# プログラミング ガイド)
*フィールド*とは、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)で直接宣言される任意の型の変数です。 フィールドは、それを含んでいる型の*メンバー*です。  
  
 クラスまたは構造体には、インスタンス フィールドと静的フィールドのいずれか、またはその両方が含まれる場合があります。 インスタンス フィールドは、型のインスタンスに固有です。 たとえば、クラス T と、そのクラスのインスタンス フィールド F があるとします。型 T のオブジェクトを 2 つ作成した場合、他方のオブジェクトの値に影響を与えることなく、各オブジェクトの F の値を変更できます。 これとは対照的に、クラス自体に属する静的フィールドは、そのクラスのすべてのインスタンスで共有されます。 インスタンス A に加えられた変更は、インスタンス B と C がフィールドにアクセスした場合、これらのインスタンスでただちに確認されます。  
  
 通常、フィールドは、プライベートまたは保護されたアクセシビリティを持つ変数に対してのみ使用します。 クラスからクライアント コードに公開するデータは、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)を使用して提供する必要があります。 これらの構成要素を使用して、内部フィールドに間接的にアクセスすることで、無効な値が入力されることを防止できます。 パブリック プロパティによって公開されるデータを格納するプライベート フィールドは、*バッキング ストア*または*バッキング フィールド*と呼ばれます。  
  
 一般に、フィールドは、複数のクラス メソッドからアクセスできるようにする必要があり、かつ 1 つのメソッドの有効期間より長く保持する必要があるデータを格納します。 たとえば、暦の日付を表すクラスには、月、日、年を表す 3 つの整数フィールドが存在します。 1 つのメソッドのスコープ外で使用されることのない変数は、メソッド本体内で*ローカル変数*として宣言する必要があります。  
  
 フィールドは、フィールドのアクセス レベル、フィールドの型、フィールドの名前の順に指定して、クラス ブロック内で宣言します。 例:  
  
 [!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 オブジェクト内のフィールドにアクセスするには、`objectname.fieldname` のように、オブジェクト名の後にピリオドを追加し、その後にフィールド名を続けます。 例:  
  
 [!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 フィールドには、フィールドの宣言時に代入演算子を使用して初期値を指定できます。 たとえば、`day` フィールドに `"Monday"` を自動的に代入するには、次の例のように `day` を宣言します。  
  
 [!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 フィールドは、オブジェクト インスタンスのコンストラクターが呼び出される直前に初期化されます。 コンストラクターがフィールドの値を代入すると、フィールドの宣言時に指定された値はすべて上書きされます。 詳細については、「[コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)」を参照してください。  
  
> [!NOTE]
>  フィールドの初期化子は、他のインスタンス フィールドを参照できません。  
  
 フィールドは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected internal` とマークできます。 これらのアクセス修飾子により、クラスのユーザーがフィールドにアクセスする方法が定義されます。 詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 必要に応じて、フィールドを[静的](../../../csharp/language-reference/keywords/static.md)に宣言することもできます。 その場合、クラスのインスタンスが存在しなくても、呼び出し元がいつでもフィールドを使用できるようになります。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 フィールドを [readonly](../../../csharp/language-reference/keywords/readonly.md) として宣言することもできます。 読み取り専用フィールドには、初期化時またはコンストラクターによる以外は、値を代入できません。 `static``readonly` フィールドは基本的に定数と同じですが、C# コンパイラが静的な読み取り専用フィールドの値にアクセスできるのは実行時のみで、コンパイル時はアクセスできない点が異なります。 詳細については、「[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
