---
title: '方法 : ファイル関連のダイアログ ボックスの自動アップグレードを無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: 380f8abe502c37e57207c43696158c1e3bdc7697
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532488"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>方法 : ファイル関連のダイアログ ボックスの自動アップグレードを無効にする
ときに、<xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>クラスは、アプリケーションで使用されて、その外観と動作は、アプリケーションが実行されている Windows のバージョンによって異なります。 アプリケーションで作成されたときに、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]に表示される前または[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]、<xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>で自動的に表示されます、[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]外観と動作します。 以降では、 [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)]、自動アップグレードを表示することを選択できます、<xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>で、 [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-外観と動作のスタイルを設定します。  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>ファイル関連のダイアログ ボックスの自動アップグレードを無効にするには  
  
1.  設定、<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>プロパティ<xref:System.Windows.Forms.OpenFileDialog>または<xref:System.Windows.Forms.SaveFileDialog>に`false` ダイアログ ボックスを表示する前にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FileDialog>
