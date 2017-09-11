---
title: "軽減策: CspParameters.ParentWindowHandle で HWND を受け取る"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- CspParameters.ParentWindowHandle
- CspParameters.ParentWindowHandle retargeting change
ms.assetid: 33264333-71d6-4d43-8827-9c98878cfea7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b65aaf7149ca29b2af3efdf44ee9489a04c73a2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a><span data-ttu-id="61735-102">軽減策: CspParameters.ParentWindowHandle で HWND を受け取る</span><span class="sxs-lookup"><span data-stu-id="61735-102">Mitigation: CspParameters.ParentWindowHandle Expects an HWND</span></span>

<span data-ttu-id="61735-103">.NET Framework 2.0 で導入された <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティをアプリケーションに使用すると、親ウィンドウのハンドル値を登録できます。これを利用して、キーにアクセスする必要がある UI (PIN プロンプトや同意を求めるダイアログなど) を、指定したウィンドウの子のモーダルとして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="61735-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property, introduced in the .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or a consent dialog) opens as a modal child to the specified window.</span></span> <span data-ttu-id="61735-104">.NET Framework 4.7 以降をターゲットとするアプリケーションでは、ウィンドウ ハンドル (HWND) をこのプロパティに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="61735-104">Starting with applications that target the .NET Framework 4.7, a window handle (HWND) can be assigned to this property.</span></span>

<span data-ttu-id="61735-105">.NET Framework 4.6.2 までの .NET Framework バージョンでは、<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティに割り当てられている値は、HWND 値があるメモリ内の場所を表す <xref:System.IntPtr> であると想定されています。</span><span class="sxs-lookup"><span data-stu-id="61735-105">In versions of the .NET Framework through the .NET Framework 4.6.2, the value assigned to the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property was expected to be an <xref:System.IntPtr> that represents the location in memory where the HWND value resided.</span></span> <span data-ttu-id="61735-106">Windows 7 以前のバージョンの Windows オペレーティング システムでは、このプロパティを `form.Handle` に設定しても影響がありませんが、Windows 8 以降のバージョンでは、<xref:System.Security.Cryptography> の結果として "パラメーターが正しくありません" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61735-106">On Windows 7 and earlier versions of the Windows operating system, setting the property to `form.Handle` had no effect, but on Windows 8 and later versions, it results in a <xref:System.Security.Cryptography> with the message, "The parameter is incorrect."</span></span>

<span data-ttu-id="61735-107">.NET Framework 4.7 を対象とするアプリ以降では、Windows フォーム アプリケーションは、次のようなコードを使用して、<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="61735-107">Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a><span data-ttu-id="61735-108">影響</span><span class="sxs-lookup"><span data-stu-id="61735-108">Impact</span></span>

<span data-ttu-id="61735-109">親ウィンドウの関係を登録する .NET Framework 4.7 以降をターゲットとするアプリケーションの場合、次のように単純な形式を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61735-109">Applications targeting the .NET Framework 4.7 or later that wish to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a><span data-ttu-id="61735-110">軽減策</span><span class="sxs-lookup"><span data-stu-id="61735-110">Mitigation</span></span>

<span data-ttu-id="61735-111">正しい値が `form.Handle` 値を保持するメモリ位置のアドレスであると特定した場合、次のように <xref:System.AppContext> スイッチ `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` を `true` に変更することでこの動作の変更を解除することができます。</span><span class="sxs-lookup"><span data-stu-id="61735-111">Developers who had identified that the correct value was the address of the memory location that held the `form.Handle` value can opt out of this change in behavior by setting the <xref:System.AppContext> switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="61735-112">プログラムで、<xref:System.AppContext> インスタンスの互換性スイッチを設定する</span><span class="sxs-lookup"><span data-stu-id="61735-112">By programmatically setting compatibility switches on the <xref:System.AppContext> instance.</span></span>

- <span data-ttu-id="61735-113">app.config ファイルの `<runtime>` セクションに以下の行を追加する:</span><span class="sxs-lookup"><span data-stu-id="61735-113">By adding the following line to the `<runtime>` section of the app.config file:</span></span>
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

<span data-ttu-id="61735-114">逆に、.NET Framework 4.7 で実行するアプリケーションには新しい動作を選択し、旧バージョンの .NET Framework バージョンをターゲットとする場合は、<xref:System.AppContext> スイッチを `false` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="61735-114">Conversely, users who wish to opt in to the new behavior for applications that run under the .NET Framework 4.7 but target an earlier version of the .NET Framework versions can set the <xref:System.AppContext> switch to `false`.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="61735-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="61735-115">See also</span></span>

[<span data-ttu-id="61735-116">.NET Framework 4.7 における再ターゲットの変更点</span><span class="sxs-lookup"><span data-stu-id="61735-116">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

