---
title: スタートアップ設定スキーマ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f344139fd7d7c84aa75ab5e17b6312f3b0c3e031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="startup-settings-schema"></a><span data-ttu-id="96c03-102">スタートアップ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="96c03-102">Startup Settings Schema</span></span>
<span data-ttu-id="96c03-103">スタートアップ設定は、アプリケーションを実行する必要のある共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="96c03-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="96c03-104">要素</span><span class="sxs-lookup"><span data-stu-id="96c03-104">Element</span></span>|<span data-ttu-id="96c03-105">説明</span><span class="sxs-lookup"><span data-stu-id="96c03-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96c03-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="96c03-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="96c03-107">バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="96c03-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="96c03-108">ランタイムのバージョン 1.1 でビルドされたアプリケーションは、**\<supportedRuntime >** 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="96c03-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="96c03-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="96c03-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="96c03-110">アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="96c03-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="96c03-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="96c03-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="96c03-112">**\<requiredRuntime>** 要素と **\<supportedRuntime>** 要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="96c03-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96c03-113">参照</span><span class="sxs-lookup"><span data-stu-id="96c03-113">See Also</span></span>  
 [<span data-ttu-id="96c03-114">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="96c03-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="96c03-115">\<PaveOver> 使用するランタイム バージョンの指定</span><span class="sxs-lookup"><span data-stu-id="96c03-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
