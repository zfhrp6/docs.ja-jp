---
title: "プロテクト メンバー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c3aacd0f08641c01200f0b1791a78413a306590
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="protected-members"></a>プロテクト メンバー
単独で保護されたメンバーはすべての機能拡張を指定しないがサブクラス化によって拡張機能をより強力な行うことができます。 メインのパブリック インターフェイスを不必要に複雑化せず、高度なカスタマイズ オプションを公開に使用できます。  
  
 フレームワークの設計者は、「保護された」名前が false 安心感を与えることができますので、プロテクト メンバーには注意する必要があります。 すべてのユーザーはサブクラス封印されていないクラスとメンバーへのアクセスが保護されているをできるパブリック メンバーに使用された守勢のコーディング方法が保護されたメンバーに適用するためすべて同じです。  
  
 **✓ を検討してください**高度なカスタマイズのメンバーを使用して保護されています。  
  
 **✓ しないで**セキュリティ、ドキュメント、および互換性分析するためにパブリックと封印されていないクラスにプロテクト メンバーを処理します。  
  
 クラスから継承するすべてのユーザーし、プロテクト メンバーにアクセスできます。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [機能拡張のための設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
