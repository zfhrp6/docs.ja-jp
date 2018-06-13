---
title: 機能拡張のデザイン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68419fe293dd25936aa3c1e3def10bbe8852e175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571385"
---
# <a name="designing-for-extensibility"></a>機能拡張のデザイン
フレームワーク設計の 1 つの重要な側面を行って、フレームワークの拡張性が慎重に考慮されていることを確認しています。 これは、コストとさまざまな機能拡張メカニズムに関連付けられている利点を理解することが必要です。 この章では、機能拡張メカニズムを判断するのに役立ちます: サブクラス化、イベント、仮想メンバー、コールバック、およびなど —、framework の要件を満たす最適なことができます。  
  
 フレームワークの機能拡張を許可する方法はたくさんあります。 コストが非常に強力に低コストの低いから範囲です。 、特定の機能拡張必要条件については、要件を満たす低コストの機能拡張メカニズムを選択してください。 通常、後で、複数の機能拡張を追加することが可能であるが、重大な変更を導入することがなく離れた実行しないことができますに注意してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [シールされていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [プロテクト メンバー](../../../docs/standard/design-guidelines/protected-members.md)  
 [イベントとコールバック](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象化 (抽象型およびインターフェイス)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [抽象化の実装用の基本クラス](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [シール](../../../docs/standard/design-guidelines/sealing.md)  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
