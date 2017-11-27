---
title: "メンバーのデザインのガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5df4ad5f6c947d8b3bf62c3bf7eb8426419e5f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="member-design-guidelines"></a>メンバーのデザインのガイドライン
メソッド、プロパティ、イベント、コンス トラクター、およびフィールドは、メンバーとしてまとめて呼ばれます。 メンバーは、最終的に、フレームワークのエンドユーザーに、フレームワークの機能が公開されている手段です。  
  
 メンバーは、仮想または非仮想、具象か抽象クラスで静的メソッドまたはインスタンスを指定でき、ユーザー補助機能のいくつかの異なるスコープを持つことができます。 このすべてのさまざまな驚異的な表現力には、同時に、フレームワーク デザイナー部分注意が必要です。  
  
 この章では、任意の型のメンバーをデザインするときに従う必要がありますの基本的なガイドラインを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [メンバーのオーバー ロード](../../../docs/standard/design-guidelines/member-overloading.md)  
 [プロパティのデザイン](../../../docs/standard/design-guidelines/property.md)  
 [コンス トラクターのデザイン](../../../docs/standard/design-guidelines/constructor.md)  
 [イベントのデザイン](../../../docs/standard/design-guidelines/event.md)  
 [フィールドのデザイン](../../../docs/standard/design-guidelines/field.md)  
 [拡張メソッド](../../../docs/standard/design-guidelines/extension-methods.md)  
 [演算子のオーバー ロード](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [パラメーターのデザイン](../../../docs/standard/design-guidelines/parameter-design.md)  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
