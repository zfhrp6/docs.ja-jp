---
title: "抽象化 (抽象型およびインターフェイス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象化 (抽象型およびインターフェイス)
抽象化では、コントラクトを記述、コントラクトの完全な実装は提供されませんする型です。 抽象化は通常インターフェイスまたは抽象クラスとして実装され、適切に定義された一連のコントラクトを実装する型の必要なセマンティクスを説明するリファレンス ドキュメントになります。 .NET Framework における最も重要な抽象化のものが<xref:System.IO.Stream>、 <xref:System.Collections.Generic.IEnumerable%601>、および<xref:System.Object>です。  
  
 抽象化のコントラクトをサポートする具象型を実装して、フレームワーク Api のかかる (で動作している) でこの具象型を使用してフレームワークを拡張することができます、抽象化します。  
  
 時間のテストに耐えることができるわかりやすいで便利な抽象化は、デザインに非常に困難です。 メインの難易度は適切ないいえが少ないと、メンバーのセットを取得しています。 抽象化のメンバーが多すぎる場合は、難しいかを実装することが不可能になります。 約束されていた機能が少なすぎますメンバーがある場合に、多くの興味深いシナリオでは役に立たなくなります。  
  
 悪影響が多すぎますの抽象化フレームワークでは、フレームワークの使いやすさに影響を与えます。 非常に具体的な実装との抽象型で動作している Api の大きい画像に適合する方法を理解することがなく抽象化を理解しにくいは多くの場合です。 また、抽象化とそのメンバーの名前は抽象的に、する多くの場合にわかりにくいつかめない最初にそれらの使用より広範なコンテキストを理解することがなくです。  
  
 ただし、抽象化は、その他の機能拡張メカニズムできない多くの場合と一致する非常に強力な機能拡張を提供します。 プラグインなど、多くのアーキテクチャのパターンの中核制御の反転 (IoC)、パイプライン、やなど。 フレームワークのテストの容易性のきわめて重要です。 適切な抽象化を使用すれば、単体テストするために大量の依存関係を消去できます。 要約すると、抽象化は、最新のオブジェクト指向フレームワークのいる豊富な機能を担当します。  
  
 **X しないで**いくつかの具体的な実装と、抽象化を使用する Api を開発してテストする場合を除き、抽象化を提供します。  
  
 **✓ しないで**抽象化を設計するときは、抽象クラスとインターフェイス間慎重に選択します。  
  
 **✓ を検討してください**抽象クラスの具象実装のテストの参照を提供します。 そのようなテストは、実装では、コントラクトを正しく実装するかどうかをテストするユーザーを許可する必要があります。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
