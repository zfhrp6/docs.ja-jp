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
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="3327a-102">システム情報と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="3327a-102">System Information and Windows Forms</span></span>
<span data-ttu-id="3327a-103">コードで意思決定を行うために、アプリケーションが実行されているコンピューターに関する情報を収集するために必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3327a-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="3327a-104">たとえば、のみ、特定のネットワークのドメインに接続されている場合に適用される関数がある可能性があります。ここでは、ドメインを確認して、ドメインが存在しない場合、関数を無効にする方法を必要があります。</span><span class="sxs-lookup"><span data-stu-id="3327a-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="3327a-105">Windows フォーム アプリケーションを使用して、<xref:System.Windows.Forms.SystemInformation>実行時に、コンピューターの点の数を決めるクラスをします。</span><span class="sxs-lookup"><span data-stu-id="3327a-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="3327a-106">次の例では、使用方法を示します、<xref:System.Windows.Forms.SystemInformation>取得するクラス、<xref:System.Windows.Forms.SystemInformation.UserName%2A>と<xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="3327a-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
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
  
 <span data-ttu-id="3327a-107">すべてのメンバー、<xref:System.Windows.Forms.SystemInformation>クラスは読み取り専用です。 ユーザーの設定を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3327a-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="3327a-108">すべてのもので、コンピューターに接続されているモニターの数から情報を返すクラスの 100 を超えるメンバーがある (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) Windows エクスプ ローラーのアイコンの間隔を (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A>と<xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>)。</span><span class="sxs-lookup"><span data-stu-id="3327a-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="3327a-109">一部のより有用なメンバーの<xref:System.Windows.Forms.SystemInformation>クラスが含まれて<xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、 <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>、および<xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>です。</span><span class="sxs-lookup"><span data-stu-id="3327a-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3327a-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3327a-110">See Also</span></span>  
 <xref:System.Windows.Forms.SystemInformation>  
 [<span data-ttu-id="3327a-111">Windows フォームでの電源管理</span><span class="sxs-lookup"><span data-stu-id="3327a-111">Power Management in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
