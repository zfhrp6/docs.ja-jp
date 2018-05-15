---
title: CoreResponseData クラス
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 640a925c3aec86b4743b1b2b62eb3793af1cc0bb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="806d6-102">CoreResponseData クラス</span><span class="sxs-lookup"><span data-stu-id="806d6-102">CoreResponseData Class</span></span>

<span data-ttu-id="806d6-103">`CoreResponseData`クラスは、HTTP ヘッダーおよび応答本文の解析を表します。</span><span class="sxs-lookup"><span data-stu-id="806d6-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="806d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="806d6-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="806d6-105">この API は、内部、およびコードで直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="806d6-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="806d6-106">代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。</span><span class="sxs-lookup"><span data-stu-id="806d6-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="806d6-107">参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。</span><span class="sxs-lookup"><span data-stu-id="806d6-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="806d6-108">Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="806d6-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="806d6-109">要件</span><span class="sxs-lookup"><span data-stu-id="806d6-109">Requirements</span></span>

<span data-ttu-id="806d6-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="806d6-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="806d6-111">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="806d6-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="806d6-112">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="806d6-112">**.NET Framework versions:** Available since 2.0.</span></span>
