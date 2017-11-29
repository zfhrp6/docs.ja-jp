---
title: "方法 : C# で定数を定義する"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ff12d0b6882289da9ed924f1c7de00edc5dc1e2e
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-define-constants-in-c"></a>方法 : C# で定数を定義する
定数とは、値がコンパイル時に設定され、変更できないフィールドです。 定数を使用して、特殊な値の数値リテラル ("マジック ナンバー") の代わりにわかりやすい名前を提供します。  
  
> [!NOTE]
>  C# では、C と C++ で通常使用される方法で、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) プリプロセッサ ディレクティブを使用して定数を定義することはできません。  
  
 整数型 (`int`、`byte` など) の定数値を定義するには、列挙型を使用します。 詳細については、「[enum](../../../csharp/language-reference/keywords/enum.md)」を参照してください。  
  
 整数型以外の定数を定義する 1 つの方法は、`Constants` という名前の 1 つの静的クラスにそれらをグループ化することです。 これを行うには、次の例に示すように、クラス名の前に定数へのすべての参照を付ける必要があります。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 クラス名修飾子を使用すると、定数を使用するユーザーは、それが定数であり、変更できないことがわかります。  
  
## <a name="see-also"></a>関連項目  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)
