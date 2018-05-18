---
title: '方法 : C# で定数を定義する'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 03912a71aba883ec9127d265e6f1a2b05e1e60fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>参照  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)
