---
title: システム情報と Windows フォーム
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: 727bcc53750081ae2d957527332ed3199c7d8e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524116"
---
# <a name="system-information-and-windows-forms"></a>システム情報と Windows フォーム
コードで意思決定を行うために、アプリケーションが実行されているコンピューターに関する情報を収集するために必要な場合があります。 たとえば、のみ、特定のネットワークのドメインに接続されている場合に適用される関数がある可能性があります。ここでは、ドメインを確認して、ドメインが存在しない場合、関数を無効にする方法を必要があります。  
  
 Windows フォーム アプリケーションを使用して、<xref:System.Windows.Forms.SystemInformation>実行時に、コンピューターの点の数を決めるクラスをします。 次の例では、使用方法を示します、<xref:System.Windows.Forms.SystemInformation>取得するクラス、<xref:System.Windows.Forms.SystemInformation.UserName%2A>と<xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 すべてのメンバー、<xref:System.Windows.Forms.SystemInformation>クラスは読み取り専用です。 ユーザーの設定を変更することはできません。 すべてのもので、コンピューターに接続されているモニターの数から情報を返すクラスの 100 を超えるメンバーがある (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) Windows エクスプ ローラーのアイコンの間隔を (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A>と<xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>)。  
  
 一部のより有用なメンバーの<xref:System.Windows.Forms.SystemInformation>クラスが含まれて<xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、 <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>、および<xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.SystemInformation>  
 [Windows フォームでの電源管理](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
