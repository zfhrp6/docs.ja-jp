---
title: "メンバー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
caps.latest.revision: 20
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 229955400c0c16cdc0069d6e45148d91d6253f9d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="members-c-programming-guide"></a>メンバー (C# プログラミング ガイド)
クラスと構造体には、そのデータおよび動作を表すメンバーがあります。 クラスのメンバーには、クラスで宣言されているすべてのメンバーと、継承の階層構造のすべてのクラスで宣言されているメンバー (コンストラクターとファイナライザーを除く) が含まれます。 基底クラスのプライベート メンバーは継承されますが、派生クラスからはアクセスできません。  
  
 クラスまたは構造体に含まれるメンバーの種類を次の表に示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)|フィールドとは、クラス スコープで宣言される変数です。 フィールドは、組み込みの数値型であったり、別のクラスのインスタンスであったりします。 たとえば、Calender クラスには、現在の日付を格納するフィールドがあります。|  
|[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)|定数とは、コンパイル時に値が設定され、設定された値を変更できないフィールドまたはプロパティです。|  
|[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)|プロパティはクラスのメソッドで、そのクラスのフィールドのようにアクセスされます。 プロパティは、クラスのフィールドを保護し、オブジェクトが認識することなくフィールドが変更されるのを防止できます。|  
|[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)|メソッドは、クラスが実行できるアクションを定義します。 メソッドは、入力データを提供するパラメーターを受け取り、パラメーターを通じて出力データを返すことができます。 メソッドは、パラメーターを使用せずに値を直接返すこともできます。|  
|[イベント](../../../csharp/programming-guide/events/index.md)|イベントは、ボタンのクリックやメソッドの正常な終了などの発生に関する通知を他のオブジェクトに提供します。 イベントを定義し、トリガーするには、デリゲートを使用します。|  
|[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|オーバーロードされた演算子は、クラス メンバーと見なされます。 演算子をオーバーロードする場合は、演算子をパブリックな静的メソッドとしてクラスに定義します。 定義済みの演算子 (`+`、`*`、`<` など) はメンバーとは見なされません。 詳細については、「[オーバーロードされた演算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)」を参照してください。|  
|[インデクサー](../../../csharp/programming-guide/indexers/index.md)|インデクサーを使用すると、配列と同じようにオブジェクトにインデックスを付けることができます。|  
|[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)|コンストラクターは、オブジェクトを初めて作成するときに呼び出されるメソッドです。 コンストラクターは、一般にオブジェクトのデータを初期化するために使用します。|  
|[ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)|ファイナライザーが C# で使用されることはほとんどありません。 デストラクターは、オブジェクトがメモリから削除されるときに、ランタイム実行エンジンによって呼び出されるメソッドです。 デストラクターは、通常、解放する必要があるリソースが適切に処理されるようにするために使用します。|  
|[入れ子にされた型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|入れ子にされた型は、別の型で宣言された型です。 入れ子にされた型は、通常、それを格納している型だけで使用されるオブジェクトを表すために使用します。|  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [入れ子にされた型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)   
 [演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [オーバーロードされた演算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
