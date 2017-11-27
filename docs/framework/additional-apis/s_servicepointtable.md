---
title: "ServicePointManager.s_ServicePointTable フィールド"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="6eec5-102">ServicePointManager.s\_ServicePointTable フィールド</span><span class="sxs-lookup"><span data-stu-id="6eec5-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="6eec5-103">`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable> HTTP のアクティブな接続の一覧を格納している (<xref:System.Net.ServicePoint>s) で、<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="6eec5-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="6eec5-104">構文</span><span class="sxs-lookup"><span data-stu-id="6eec5-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="6eec5-105">`ServicePointManager.s_ServicePointTable`フィールドはプライベートであり、コード内で直接使用します。</span><span class="sxs-lookup"><span data-stu-id="6eec5-105">The `ServicePointManager.s_ServicePointTable` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="6eec5-106">Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6eec5-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6eec5-107">要件</span><span class="sxs-lookup"><span data-stu-id="6eec5-107">Requirements</span></span>

<span data-ttu-id="6eec5-108">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6eec5-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6eec5-109">**アセンブリ:**システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="6eec5-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6eec5-110">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="6eec5-110">**.NET Framework versions:** Available since 2.0.</span></span>
