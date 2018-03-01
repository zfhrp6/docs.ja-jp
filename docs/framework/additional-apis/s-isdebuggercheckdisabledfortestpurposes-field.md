---
title: "s_isDebuggerCheckDisabledForTestPurposes フィールド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.workload:
- dotnet
ms.openlocfilehash: 67da38d958d153ebe526f298785b39afb7be6513
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="aff90-102">s_isDebuggerCheckDisabledForTestPurposes フィールド</span><span class="sxs-lookup"><span data-stu-id="aff90-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="aff90-103">このプライベート フィールドで、`System.Windows.Diagnostics.VisualDiagnostics`クラスは、内部のアクティブなデバッガーのチェックを実行するかどうかを決定する Visual Studio によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="aff90-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="aff90-104">構文</span><span class="sxs-lookup"><span data-stu-id="aff90-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="aff90-105">API で、`System.Windows.Diagnostics.VisualDiagnostics`クラスは、デバッガーの下で、アプリケーションが実行されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aff90-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="aff90-106">設定`s_isDebuggerCheckDisabledForTestPurposes`に`true`デバッガーの外部の Api にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="aff90-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="aff90-107">Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="aff90-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="aff90-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="aff90-108">Requirements</span></span>

<span data-ttu-id="aff90-109">**Namespace:**<xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="aff90-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="aff90-110">**アセンブリ:** PresentationCore.dll) の「PresentationCore</span><span class="sxs-lookup"><span data-stu-id="aff90-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="aff90-111">**.NET framework のバージョン:** 4.6 以降の利用可能です。</span><span class="sxs-lookup"><span data-stu-id="aff90-111">**.NET Framework versions:** Available since 4.6.</span></span>
