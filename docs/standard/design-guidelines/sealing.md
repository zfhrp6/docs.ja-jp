---
title: "シール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39bb29d36b6d81464b1213ebc0bf7aee6ceb5713
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="sealing"></a>シール
オブジェクト指向フレームワークの機能の 1 つは、開発者が拡張およびフレームワークの設計者によって予期しない方法でカスタマイズできます。 これは、両方の電源および拡張可能なデザインの危険性です。 フレームワークをデザインするときは、そのため、非常に重要が必要な場合、機能拡張を慎重に設計して危険である場合は、機能拡張を制限します。  
  
 拡張機能のことを防ぐ強力なメカニズムをシールするとします。 クラスまたは個々 のメンバーのいずれかを封印することができます。 クラスをシールすると、ユーザーがクラスから継承できなくなります。 メンバーをシールすると、ユーザーが特定のメンバーをオーバーライドするできなくなります。  
  
 **X しないで**これを行うには相応の理由をしなくてもクラスをシールします。  
  
 機能拡張シナリオを検討することはできませんので、クラスをシールが妥当な理由です。 Framework ユーザーなどの便利なメンバーの追加など、さまざまな明確な理由のクラスから継承します。 参照してください[封印されていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)明確な理由の例についてはユーザーが、型から継承します。  
  
 クラスをシールする理由は次のとおりです。  
  
-   クラスは、静的クラスです。 参照してください[静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)です。  
  
-   クラスは、継承されたプロテクト メンバーにセキュリティ上重要な機密情報を格納します。  
  
-   クラスは多くの仮想メンバーを継承し、それらを個別に封印のコストは封印されていないクラスを残すことの利点を上回ります。  
  
-   クラスは、非常に高速なランタイム ルックアップが必要な属性です。 Sealed 属性では、封印されていないものよりもわずかに高いパフォーマンス レベルがあります。 参照してください[属性](../../../docs/standard/design-guidelines/attributes.md)です。  
  
 **X しないで**sealed 型でプロテクト メンバーまたは仮想メンバーを宣言します。  
  
 定義上、シールされた型から継承できません。 つまり、sealed 型でプロテクト メンバーを呼び出すことはできません、sealed 型で仮想メソッドをオーバーライドすることはできません。  
  
 **✓ を検討してください**をオーバーライドするメンバーをシールします。  
  
 仮想メンバーの概要に起因する問題 (で説明した[仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)) 若干程度が同様に、上書きを適用します。 上書きが封印、継承階層の時点からこれらの問題から保護します。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [シールされていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)
