---
title: HttpWebRequest._CoreResponse Field
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6493747cf6c894357223f011da026770778e26c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="f794f-102">HttpWebRequest です。\_CoreResponse フィールド</span><span class="sxs-lookup"><span data-stu-id="f794f-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="f794f-103">`HttpWebRequest._CoreResponse`オブジェクトは、(どちらか、 [CoreResponseData](coreresponsedata.md)または<xref:System.Exception>) の HTTP 応答の解析結果を含むです。</span><span class="sxs-lookup"><span data-stu-id="f794f-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="f794f-104">構文</span><span class="sxs-lookup"><span data-stu-id="f794f-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="f794f-105">この API は、コード内で直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="f794f-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="f794f-106">代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。</span><span class="sxs-lookup"><span data-stu-id="f794f-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="f794f-107">参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。</span><span class="sxs-lookup"><span data-stu-id="f794f-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="f794f-108">Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f794f-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f794f-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="f794f-109">Requirements</span></span>

<span data-ttu-id="f794f-110">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f794f-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f794f-111">**アセンブリ:**システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="f794f-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f794f-112">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="f794f-112">**.NET Framework versions:** Available since 2.0.</span></span>
