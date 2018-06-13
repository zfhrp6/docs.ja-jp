---
title: UI オートメーションのセキュリティの概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 293cee72e80e88215fccb3902eb88963814cb2ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400199"
---
# <a name="ui-automation-security-overview"></a><span data-ttu-id="8598e-102">UI オートメーションのセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="8598e-102">UI Automation Security Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="8598e-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="8598e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8598e-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8598e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8598e-105">この概要では、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] における [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]のセキュリティ モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8598e-105">This overview describes the security model for [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].</span></span>  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a><span data-ttu-id="8598e-106">ユーザー アカウント制御</span><span class="sxs-lookup"><span data-stu-id="8598e-106">User Account Control</span></span>  
 <span data-ttu-id="8598e-107">セキュリティは [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] の重要点であり、とりわけ顕著な革新として、より高い特権が必要なアプリケーションとサービスの実行を必ずしもブロックされずに、(管理者以外の) 標準ユーザーとして実行する能力が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="8598e-107">Security is a major focus of [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] and among the innovations is the ability for users to run as standard (non-administrator) users without necessarily being blocked from running applications and services that require higher privileges.</span></span>  
  
 <span data-ttu-id="8598e-108">[!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]では、ほとんどのアプリケーションに、標準トークンまたは管理トークンのいずれかが付属しています。</span><span class="sxs-lookup"><span data-stu-id="8598e-108">In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], most applications are supplied with either a standard or an administrative token.</span></span> <span data-ttu-id="8598e-109">アプリケーションが管理アプリケーションとして識別できない場合は、既定で標準のアプリケーションとして起動されます。</span><span class="sxs-lookup"><span data-stu-id="8598e-109">If an application cannot be identified as an administrative application, it is launched as a standard application by default.</span></span> <span data-ttu-id="8598e-110">管理アプリケーションとして識別されたアプリケーションが起動される前に、 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] は、昇格された権限でアプリケーションを実行することへの同意をユーザーに求めるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="8598e-110">Before an application identified as administrative can be launched, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] prompts the user for consent to run the application as elevated.</span></span> <span data-ttu-id="8598e-111">ユーザーがローカル管理者グループのメンバーである場合でも、同意を求めるメッセージは既定で表示されます。これは、管理者の資格情報を必要とするアプリケーションまたはシステム コンポーネントが実行の許可を要求するまで、管理者は標準ユーザーとして実行するためです。</span><span class="sxs-lookup"><span data-stu-id="8598e-111">The consent prompt is displayed by default, even if the user is a member of the local Administrators group, because administrators run as standard users until an application or system component that requires administrative credentials requests permission to run.</span></span>  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a><span data-ttu-id="8598e-112">より高い特権が必要なタスク</span><span class="sxs-lookup"><span data-stu-id="8598e-112">Tasks Requiring Higher Privileges</span></span>  
 <span data-ttu-id="8598e-113">管理者特権が必要なタスクをユーザーが実行しようとする場合、 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] はユーザーに続行に同意するかを確認するダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="8598e-113">When a user attempts to perform a task that requires administrative privileges, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] presents a dialog box asking the user for consent to continue.</span></span> <span data-ttu-id="8598e-114">このダイアログ ボックスは、悪意のあるソフトウェアがユーザー入力をシミュレートできないように、プロセス間通信から保護されます。</span><span class="sxs-lookup"><span data-stu-id="8598e-114">This dialog box is protected from cross-process communication, so that malicious software cannot simulate user input.</span></span> <span data-ttu-id="8598e-115">同様に、デスクトップのログオン画面は、通常は他のプロセスからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="8598e-115">Similarly, the desktop logon screen cannot normally be accessed by other processes.</span></span>  
  
 <span data-ttu-id="8598e-116">UI オートメーション クライアントは、他のプロセスと通信する必要があります。プロセスによっては、より高い特権レベルで実行している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8598e-116">UI Automation clients must communicate with other processes, some of them perhaps running at a higher privilege level.</span></span> <span data-ttu-id="8598e-117">クライアントにも、通常は他のプロセスによって表示できないシステム ダイアログ ボックスへのアクセスが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8598e-117">Clients also might need access to the system dialog boxes that are not normally visible to other processes.</span></span> <span data-ttu-id="8598e-118">そのため、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クライアントはシステムによって信頼されている必要があり、特別な特権で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8598e-118">Therefore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clients must be trusted by the system, and must run with special privileges.</span></span>  
  
 <span data-ttu-id="8598e-119">より高い権限レベルで実行されているアプリケーションと通信する信頼を得るためには、アプリケーションに署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8598e-119">To be trusted to communicate with applications running at a higher privilege level, applications must be signed.</span></span>  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a><span data-ttu-id="8598e-120">マニフェスト ファイル</span><span class="sxs-lookup"><span data-stu-id="8598e-120">Manifest Files</span></span>  
 <span data-ttu-id="8598e-121">保護されたシステム [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]にアクセスするためには、マニフェスト ファイル内に特別な属性が含まれるマニフェスト ファイルを使ってアプリケーションをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8598e-121">To gain access to the protected system [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], applications must be built with a manifest file that includes a special attribute in the manifest file.</span></span> <span data-ttu-id="8598e-122">次のように、この `uiAccess` 属性は `requestedExecutionLevel` タグに含まれます。</span><span class="sxs-lookup"><span data-stu-id="8598e-122">This `uiAccess` attribute is included in the `requestedExecutionLevel` tag, as follows:</span></span>  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 <span data-ttu-id="8598e-123">このコードの `level` 属性の値は一例にすぎません。</span><span class="sxs-lookup"><span data-stu-id="8598e-123">The value of the `level` attribute in this code is an example only.</span></span>  
  
 <span data-ttu-id="8598e-124">既定では`UIAccess` は "false" です。つまり、属性を省略した場合、またはアセンブリのマニフェストが存在しない場合、アプリケーションは保護された [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="8598e-124">`UIAccess` is "false" by default; that is, if the attribute is omitted, or if there is no manifest for the assembly, the application will not be able to gain access to protected [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="8598e-125">[!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] セキュリティ、アプリケーションの署名、およびアセンブリ マニフェストの作成の詳細については、  [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp)の「最小限の特権環境での開発者向けアプリケーションのベスト プラクティスとガイドライン」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8598e-125">For more information on [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] security, on signing applications, and on creating assembly manifests, see "Developer Best Practices and Guidelines for Applications in a Least Privileged Environment" on  [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).</span></span>
