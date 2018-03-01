---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9057eabb7e3dfdfaa872fbcf2fe1180d0bbc7920
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="2917a-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) メソッド</span><span class="sxs-lookup"><span data-stu-id="2917a-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="2917a-103">[.NET Framework 4.5.1 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="2917a-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="2917a-104">特定のストリームをランダム アクセス ストリームに変換します。</span><span class="sxs-lookup"><span data-stu-id="2917a-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="2917a-105">**Namespace:**<xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2917a-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="2917a-106">**アセンブリ:** System.Runtime.WindowsRuntime (system.runtime.windowsruntime.dll 内)</span><span class="sxs-lookup"><span data-stu-id="2917a-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2917a-107">構文</span><span class="sxs-lookup"><span data-stu-id="2917a-107">Syntax</span></span>  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2917a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2917a-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="2917a-109">型: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2917a-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="2917a-110">変換するストリーム。</span><span class="sxs-lookup"><span data-stu-id="2917a-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2917a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="2917a-111">Return Value</span></span>  
 <span data-ttu-id="2917a-112">型: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="2917a-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="2917a-113">A[!INCLUDE[wrt](../../../includes/wrt-md.md)]ランダム アクセス ストリームは、変換されたストリームを表します。</span><span class="sxs-lookup"><span data-stu-id="2917a-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="2917a-114">例外</span><span class="sxs-lookup"><span data-stu-id="2917a-114">Exceptions</span></span>  
  
|<span data-ttu-id="2917a-115">例外</span><span class="sxs-lookup"><span data-stu-id="2917a-115">Exception</span></span>|<span data-ttu-id="2917a-116">状態</span><span class="sxs-lookup"><span data-stu-id="2917a-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="2917a-117">変換するストリームがシークをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2917a-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2917a-118">解説</span><span class="sxs-lookup"><span data-stu-id="2917a-118">Remarks</span></span>  
 <span data-ttu-id="2917a-119">この拡張メソッドは、Windows ストア アプリを開発する場合のみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="2917a-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="2917a-120">このメソッドは、Windows ストア アプリのストリームを使用する便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="2917a-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="2917a-121">変換する .NET Framework ストリームはシークをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2917a-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="2917a-122">詳細については、<xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2917a-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2917a-123">この API は .NET Framework 4.5.1 以上ではサポートされますが、Version 4.5 ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2917a-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="2917a-124">バージョン情報</span><span class="sxs-lookup"><span data-stu-id="2917a-124">Version Information</span></span>  
 <span data-ttu-id="2917a-125">**Windows ストア アプリ用 .NET**</span><span class="sxs-lookup"><span data-stu-id="2917a-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="2917a-126">Windows 8.1 でサポート</span><span class="sxs-lookup"><span data-stu-id="2917a-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2917a-127">参照</span><span class="sxs-lookup"><span data-stu-id="2917a-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="2917a-128">方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う</span><span class="sxs-lookup"><span data-stu-id="2917a-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
