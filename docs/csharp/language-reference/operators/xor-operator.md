---
title: ^ 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271251"
---
# <a name="-operator-c-reference"></a>^ 演算子 (C# リファレンス)
整数型と `bool` には、2 項 `^` 演算子が事前定義されています。 整数型の場合、`^` はそのオペランドのビット演算排他的 OR を計算します。 `bool` オペランドの場合、`^` はそのオペランドの論理排他的 OR を計算します。つまり、そのオペランドの厳密に 1 つが `true` の場合およびその場合に限って、結果が `true` になります。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `^` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 前の例における `0xf8 ^ 0x3f` の計算では、16 進値の F8 と 3F に対応する次の 2 つのバイナリ値にビット演算排他的 OR が実行されます。  
  
 `1111 1000`  
  
 `0011 1111`  
  
 排他的 OR の結果は `1100 0111` であり、16 進値の C7 です。  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
