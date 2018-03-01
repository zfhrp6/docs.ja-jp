---
title: "Connection.m_WriteList フィールド"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3849fdd327923e480cd88c932cfdce6580d3f09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="aa179-102">Connection.m\_WriteList フィールド</span><span class="sxs-lookup"><span data-stu-id="aa179-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="aa179-103">`Connection.m_WriteList`<xref:System.Collections.ArrayList>の<xref:System.Net.HttpWebRequest>はキューに入れ HTTP 経由で送信するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="aa179-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa179-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa179-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="aa179-105">`Connection.m_WriteList`フィールドはプライベートであり、コード内で直接使用します。</span><span class="sxs-lookup"><span data-stu-id="aa179-105">The `Connection.m_WriteList` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="aa179-106">Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="aa179-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa179-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="aa179-107">Requirements</span></span>

<span data-ttu-id="aa179-108">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="aa179-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="aa179-109">**アセンブリ:**システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="aa179-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="aa179-110">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="aa179-110">**.NET Framework versions:** Available since 2.0.</span></span>
