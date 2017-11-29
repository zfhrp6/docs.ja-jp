---
title: "抽象化の実装用の基本クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c8cd779dba0e7ce559e29af7b16bf04b3d0dc2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="base-classes-for-implementing-abstractions"></a>抽象化の実装用の基本クラス
厳密には、別のクラスがそこから派生したときに、クラスは、基本クラスになります。 このセクションの目的で、基本クラスが主に、共通の抽象化を指定するか、一部を再利用する他のクラスの既定の実装が継承に設計されたクラスです。 基本クラスは、通常、階層のルートに抽象化と下部にいくつかのカスタム実装の間の継承階層の途中で配置できます。  
  
 これらは、抽象化を実装するための実装のヘルパーとして機能します。 たとえば、項目の順序付けられたコレクションのフレームワークの抽象化の 1 つは、<xref:System.Collections.Generic.IList%601>インターフェイスです。 実装する<xref:System.Collections.Generic.IList%601>は重要でとなるため、フレームワーク、いくつかの基底クラスなど<xref:System.Collections.ObjectModel.Collection%601>と<xref:System.Collections.ObjectModel.KeyedCollection%602>、カスタム コレクションを実装するためのヘルパーとして機能します。  
  
 基底クラスは通常、単独で抽象化として機能するのに適したが多すぎる実装を格納する傾向があるためです。 たとえば、`Collection<T>`基底クラスには、非ジェネリックによって実装されているファクトに関連する実装の多数が含まれている`IList`(非ジェネリック コレクションをより深く統合) へのインターフェイスし、であることを項目のコレクションが格納されています。そのフィールドのいずれかでメモリ。  
  
 前述のとおり、基本クラスは抽象化を実装する必要があるユーザーの貴重なヘルプを提供することができますが、同時に可能性がある重大な責任です。 継承階層の深さを向上し、ので概念的フレームワークが複雑になる、サーフェス領域を追加します。 そのため、フレームワークのユーザーに重要な価値を提供する場合にのみ、基本クラスを使用してください。 これらを基本クラスから継承の代わりに内部実装に大文字に委任する必要があることを検討する framework の実装時にのみ値を提供する場合に避ける必要があります。  
  
 **✓ を検討してください**抽象メンバーが含まれている場合でも、基本クラスの抽象です。 これをユーザーに明確に伝達するクラスは継承するためだけに設計されています。  
  
 **✓ を検討してください**主要なシナリオの種類から別の名前空間の基本クラスを配置することです。 定義では、基底クラスは高度な機能拡張シナリオのためのものし、そのため、大半のユーザーに重要ではありません。  
  
 **避け x**クラスは、パブリック Api で使用する場合は、"Base"サフィックスを持つ基本クラスを名前付けします。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [機能拡張のための設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
