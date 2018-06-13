---
title: 接続クラス
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 7423136ab8e04c076e3e5e33efdf010f36d02242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349634"
---
# <a name="connection-class"></a><span data-ttu-id="315cc-102">接続クラス</span><span class="sxs-lookup"><span data-stu-id="315cc-102">Connection Class</span></span>

<span data-ttu-id="315cc-103">`Connection`クラス解析サーバーの応答、要求をキュー、およびパイプライン要求します。</span><span class="sxs-lookup"><span data-stu-id="315cc-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="315cc-104">構文</span><span class="sxs-lookup"><span data-stu-id="315cc-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="315cc-105">`Connection`クラスは内部と、コード内で直接使用します。</span><span class="sxs-lookup"><span data-stu-id="315cc-105">The `Connection` class is internal and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="315cc-106">Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="315cc-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="315cc-107">要件</span><span class="sxs-lookup"><span data-stu-id="315cc-107">Requirements</span></span>

<span data-ttu-id="315cc-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="315cc-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="315cc-109">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="315cc-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="315cc-110">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="315cc-110">**.NET Framework versions:** Available since 2.0.</span></span>
