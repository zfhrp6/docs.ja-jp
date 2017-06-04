---
title: "方法 : ファイル関連のダイアログ ボックスの自動アップグレードを無効にする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "自動アップグレード不参加 OpenFileDialog [Windows フォーム]"
  - "[ファイル] ダイアログ ボックス [Windows フォーム] で、自動アップグレードを無効"
  - "Windows Vista のファイル ダイアログ ボックスで、自動アップグレードを無効"
  - "自動アップグレード不参加 SaveFileDialog [Windows フォーム]"
  - "AutoUpgradeEnabled プロパティ"
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : ファイル関連のダイアログ ボックスの自動アップグレードを無効にする
ときに、 <xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>クラス、アプリケーションで使用して、その外観と動作は、アプリケーションが実行されている Windows のバージョンによって異なります。 アプリケーションで作成されたときに、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]に表示される前または[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]、 <xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>で自動的に表示されます、[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外観と動作します。 以降では、 [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)]、表示する自動アップグレードを避けることができます、 <xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>で、 [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-スタイルの外観と動作します。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>ファイル ダイアログ ボックスの自動アップグレードしないことを  
  
1.  設定、 <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>の<xref:System.Windows.Forms.OpenFileDialog>または<xref:System.Windows.Forms.SaveFileDialog>に`false` ダイアログ ボックスを表示する前にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FileDialog>