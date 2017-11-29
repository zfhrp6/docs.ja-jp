---
title: "アセンブリと DLL の名前"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 071ca1547898b80440e86df0e4cb9c0667e462ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-assemblies-and-dlls"></a>アセンブリと DLL の名前
アセンブリは、展開とマネージ コード アプリケーションの id の単位です。 アセンブリは、1 つまたは複数のファイルにまたがることができますが通常アセンブリは一対一、DLL にマップされます。 そのため、このセクションでは、のみ DLL の名前付け規則、アセンブリの名前付け規則にマップすることができますがについて説明します。  
  
 **✓ しないで**アセンブリ System.Data などの機能の大きなチャンクを提案する Dll の名前を選択します。  
  
 アセンブリ名と DLL 名を名前空間の名前に対応する必要はありませんが、これはアセンブリの名前を付けるときは、名前空間の名前を次に適切です。 適切な経験則では、アセンブリに含まれるアセンブリの共通のプレフィックスに基づく DLL の名前です。 たとえば、2 つの名前空間を持つアセンブリ`MyCompany.MyTechnology.FirstFeature`と`MyCompany.MyTechnology.SecondFeature`、呼び出すことが`MyCompany.MyTechnology.dll`です。  
  
 **✓ を検討してください**Dll を次のパターンに従って名前付け。  
  
 `<Company>.<Component>.dll`  
  
 ここで`<Component>`ドットで区切られた 1 つ以上の句が含まれています。 例:  
  
 `Litware.Controls.dll`。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
