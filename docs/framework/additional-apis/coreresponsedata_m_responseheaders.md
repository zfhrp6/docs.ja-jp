---
title: CoreResponseData.m_ResponseHeaders フィールド
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: ea93b70ae8e1a710b4208050d7ec823a28b218b7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="coreresponsedatamresponseheaders-field"></a><span data-ttu-id="b49bd-102">CoreResponseData.m\_ResponseHeaders フィールド</span><span class="sxs-lookup"><span data-stu-id="b49bd-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="b49bd-103">`CoreResponseData.m_ResponseHeaders` <xref:System.Net.WebHeaderCollection>のサーバーの応答に関連付けられたヘッダー。</span><span class="sxs-lookup"><span data-stu-id="b49bd-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="b49bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="b49bd-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="b49bd-105">この API は、コード内で直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="b49bd-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="b49bd-106">代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。</span><span class="sxs-lookup"><span data-stu-id="b49bd-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="b49bd-107">参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。</span><span class="sxs-lookup"><span data-stu-id="b49bd-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="b49bd-108">Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b49bd-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b49bd-109">要件</span><span class="sxs-lookup"><span data-stu-id="b49bd-109">Requirements</span></span>

<span data-ttu-id="b49bd-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b49bd-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b49bd-111">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="b49bd-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b49bd-112">**.NET framework のバージョン:** 2.0 から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="b49bd-112">**.NET Framework versions:** Available since 2.0.</span></span>
