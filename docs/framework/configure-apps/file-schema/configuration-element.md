---
title: '&lt;構成&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d75b25734b92df062d3dc46824da44883ab46d5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-element"></a><span data-ttu-id="bcdd3-102">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="bcdd3-102">\<configuration> element</span></span>

<span data-ttu-id="bcdd3-103">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="bcdd3-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="bcdd3-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bcdd3-105">構文</span><span class="sxs-lookup"><span data-stu-id="bcdd3-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="bcdd3-106">属性</span><span class="sxs-lookup"><span data-stu-id="bcdd3-106">Attributes</span></span>

<span data-ttu-id="bcdd3-107">なし</span><span class="sxs-lookup"><span data-stu-id="bcdd3-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="bcdd3-108">親要素</span><span class="sxs-lookup"><span data-stu-id="bcdd3-108">Parent element</span></span>

<span data-ttu-id="bcdd3-109">なし</span><span class="sxs-lookup"><span data-stu-id="bcdd3-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="bcdd3-110">子要素</span><span class="sxs-lookup"><span data-stu-id="bcdd3-110">Child elements</span></span>

|     | <span data-ttu-id="bcdd3-111">説明</span><span class="sxs-lookup"><span data-stu-id="bcdd3-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bcdd3-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="bcdd3-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="bcdd3-113">構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="bcdd3-114">**\<スタートアップ >** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="bcdd3-115">スタートアップ設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-116">**\<ランタイム >** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="bcdd3-117">ランタイム設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-118">**\<system.runtime.remoting >** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="bcdd3-119">リモート処理設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-120">**\<system.Net >** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="bcdd3-121">ネットワーク設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-122">**\<cryptographySettings >** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="bcdd3-123">暗号設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-124">**\<構成 >** セクション スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="bcdd3-125">構成セクションの設定のスキーマ内のすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-126">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="bcdd3-127">トレースおよびデバッグ設定のスキーマ内のすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="bcdd3-128">[ASP.NET の構成設定スキーマ](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="bcdd3-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="bcdd3-129">ASP.NET Web サイトおよびアプリケーションを構成する要素を含む ASP.NET 設定スキーマ内のすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="bcdd3-130">使用される*Web.config*ファイル。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="bcdd3-131">**\<webServices >** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="bcdd3-132">Web サービスの設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="bcdd3-133">Web 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="bcdd3-134">IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="bcdd3-135">使用される*aspnet.config*ファイル。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bcdd3-136">コメント</span><span class="sxs-lookup"><span data-stu-id="bcdd3-136">Remarks</span></span>

<span data-ttu-id="bcdd3-137">各構成ファイルには、1 つだけ含める必要があります**\<構成 >** 要素。</span><span class="sxs-lookup"><span data-stu-id="bcdd3-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcdd3-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcdd3-138">See also</span></span>

[<span data-ttu-id="bcdd3-139">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="bcdd3-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
