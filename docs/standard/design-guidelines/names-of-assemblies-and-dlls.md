---
title: "アセンブリと Dll の名前 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Dll の名前 [.NET Framework]"
  - "アセンブリの名前 [.NET Framework]"
  - "アセンブリ [.NET Framework] の名前"
  - "Dll 名"
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# アセンブリと Dll の名前
アセンブリは、配置とマネージ コード アプリケーションの id の単位です。 アセンブリは、1 つまたは複数のファイルにまたがることができます、通常このアセンブリは、DLL と一対一をマップします。 そのため、このセクションでは、のみ DLL の名前付け規則、その後、アセンブリの名前付け規則にマップできますがについて説明します。  
  
 **✓ は** アセンブリ System.Data などの機能の大きなチャンクを提案する Dll の名前を選択します。  
  
 アセンブリと DLL の名前、名前空間の名前に対応する必要はありませんが、アセンブリの名前を付けるときは、名前空間の名前を以下にすることができます。 適切な経験則では、アセンブリに含まれるアセンブリの共通のプレフィックスに基づいた DLL の名前です。 たとえば、2 つの名前空間を持つアセンブリ `MyCompany.MyTechnology.FirstFeature` と `MyCompany.MyTechnology.SecondFeature`, を呼び出す `MyCompany.MyTechnology.dll`します。  
  
 **✓ を検討してください** Dll を次のパターンに従って名前付け。  
  
 `<Company>.<Component>.dll`  
  
 ここで `<Component>` ピリオドで区切られた 1 つまたは複数の句が含まれています。 例:  
  
 `Litware.Controls.dll`。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)