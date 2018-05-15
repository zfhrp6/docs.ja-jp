---
title: スタートアップ設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 59f0441b79244eb529be338495c32af886a5f2b3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="startup-settings-schema"></a><span data-ttu-id="c5213-102">スタートアップ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c5213-102">Startup Settings Schema</span></span>
<span data-ttu-id="c5213-103">スタートアップ設定は、アプリケーションを実行する必要のある共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5213-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="c5213-104">要素</span><span class="sxs-lookup"><span data-stu-id="c5213-104">Element</span></span>|<span data-ttu-id="c5213-105">説明</span><span class="sxs-lookup"><span data-stu-id="c5213-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5213-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="c5213-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="c5213-107">バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5213-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="c5213-108">ランタイムのバージョン 1.1 でビルドされたアプリケーションは、**\<supportedRuntime >** 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5213-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="c5213-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="c5213-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="c5213-110">アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="c5213-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="c5213-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="c5213-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="c5213-112">**\<requiredRuntime>** 要素と **\<supportedRuntime>** 要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="c5213-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5213-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5213-113">See Also</span></span>  
 [<span data-ttu-id="c5213-114">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="c5213-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c5213-115">\<PaveOver> 使用するランタイム バージョンの指定</span><span class="sxs-lookup"><span data-stu-id="c5213-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
