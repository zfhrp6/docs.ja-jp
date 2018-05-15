---
title: Connection.m_WriteList フィールド
ms.date: 05/01/2017
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
ms.openlocfilehash: d145f6fd21989ada49a581ebf2694dcd56d94351
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="c9638-102">Connection.m\_WriteList フィールド</span><span class="sxs-lookup"><span data-stu-id="c9638-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="c9638-103">`Connection.m_WriteList` <xref:System.Collections.ArrayList>の<xref:System.Net.HttpWebRequest>はキューに入れ HTTP 経由で送信するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c9638-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9638-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9638-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="c9638-105">`Connection.m_WriteList`フィールドはプライベートであり、コード内で直接使用します。</span><span class="sxs-lookup"><span data-stu-id="c9638-105">The `Connection.m_WriteList` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="c9638-106">Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c9638-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9638-107">要件</span><span class="sxs-lookup"><span data-stu-id="c9638-107">Requirements</span></span>

<span data-ttu-id="c9638-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="c9638-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="c9638-109">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="c9638-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="c9638-110">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="c9638-110">**.NET Framework versions:** Available since 2.0.</span></span>
