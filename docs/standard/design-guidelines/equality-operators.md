---
title: 等値演算子
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cd740e9b7a5d38229b3564bfeca003fc4d189624
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="equality-operators"></a>等値演算子
このセクションでは、オーバー ロードの等値演算子について説明しを指す`operator==`と`operator!=`等値演算子として。  
  
 **X しないで**等値演算子および以外のいずれかのオーバー ロードします。  
  
 **✓ しないで**いることを確認<xref:System.Object.Equals%2A?displayProperty=nameWithType>等値演算子は、同じセマンティクスと同様のパフォーマンス特性があるとします。  
  
 多くの場合、つまり`Object.Equals`等値演算子はオーバー ロード時に上書きする必要があります。  
  
 **避け x**等値演算子から例外をスローします。  
  
 たとえば、引数のいずれかがスローする代わりに null の場合は false を返す`NullReferenceException`です。  
  
## <a name="equality-operators-on-value-types"></a>値型で等値演算子  
 **✓ しないで**等しいかどうかがわかりやすい場合は、値型で等値演算子をオーバー ロードします。  
  
 ほとんどのプログラミング言語での既定の実装はありません`operator==`値型です。  
  
## <a name="equality-operators-on-reference-types"></a>参照型で等値演算子  
 **避け x**変更可能な参照型で等値演算子のオーバー ロードします。  
  
 多くの言語では、参照型の組み込みの等値演算子があります。 組み込み演算子は通常の参照の等価性を実装し、値の等価性を既定の動作が変更されたときに、多くの開発者は驚くします。  
  
 不変より参照の等価性と値の等価性の間の違いに注意をはるかに困難になるために、変更できない参照型のこの問題が軽減されます。  
  
 **避け x**実装では、参照の等価性の場合よりもはるかに低速になる場合は、参照型で等値演算子をオーバー ロードします。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
