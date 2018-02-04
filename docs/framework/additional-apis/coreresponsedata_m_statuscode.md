---
title: "CoreResponseData.m_StatusCode フィールド"
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_StatusCode
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 1630fe66152925120f5459276899b1d3e581f05e
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="coreresponsedatamstatuscode-field"></a><span data-ttu-id="2d039-102">CoreResponseData.m\_StatusCode フィールド</span><span class="sxs-lookup"><span data-stu-id="2d039-102">CoreResponseData.m\_StatusCode Field</span></span>

<span data-ttu-id="2d039-103">`CoreResponseData.m_StatusCode`<xref:System.Net.HttpStatusCode>応答のステータスを含むです。</span><span class="sxs-lookup"><span data-stu-id="2d039-103">`CoreResponseData.m_StatusCode` is an <xref:System.Net.HttpStatusCode> containing the status of the response.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d039-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d039-104">Syntax</span></span>
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> <span data-ttu-id="2d039-105">この API は、コード内で直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="2d039-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="2d039-106">代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。</span><span class="sxs-lookup"><span data-stu-id="2d039-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="2d039-107">参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d039-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="2d039-108">Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2d039-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d039-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="2d039-109">Requirements</span></span>

<span data-ttu-id="2d039-110">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="2d039-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="2d039-111">**アセンブリ:**システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="2d039-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="2d039-112">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="2d039-112">**.NET Framework versions:** Available since 2.0.</span></span>
