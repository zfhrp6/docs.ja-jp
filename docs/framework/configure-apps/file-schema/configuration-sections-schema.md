---
title: 構成セクション スキーマ
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: edd2b2e11b02d69b7bba7c3cc7d8a9a0814e0c51
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="91a60-102">構成セクション スキーマ</span><span class="sxs-lookup"><span data-stu-id="91a60-102">Configuration sections schema</span></span>

<span data-ttu-id="91a60-103">構成セクション スキーマには、構成ファイル内のカスタム設定を定義する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91a60-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="91a60-104">構成ファイルとスキーマの概要については、次を参照してください。 [、.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="91a60-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="91a60-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="91a60-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="91a60-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="91a60-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="91a60-107">[**\<オフ >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="91a60-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="91a60-108">[**\<削除 >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="91a60-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="91a60-109">[**\<セクション >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="91a60-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="91a60-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="91a60-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="91a60-111">説明</span><span class="sxs-lookup"><span data-stu-id="91a60-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="91a60-112">**\<オフ >** の **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="91a60-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="91a60-113">以前に定義されたセクションおよびセクション グループのすべてをクリアします。</span><span class="sxs-lookup"><span data-stu-id="91a60-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="91a60-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="91a60-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="91a60-115">以前に定義されたセクションおよびセクション グループのすべてをクリアします。</span><span class="sxs-lookup"><span data-stu-id="91a60-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="91a60-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="91a60-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="91a60-117">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91a60-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="91a60-118">**\<削除 >** の **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="91a60-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="91a60-119">定義済みのセクション、またはセクション グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="91a60-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="91a60-120">**\<セクション >** の **\<configSections >** と **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="91a60-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="91a60-121">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91a60-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="91a60-122">**\<sectionGroup >** の **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="91a60-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="91a60-123">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="91a60-123">Defines a namespace for configuration sections.</span></span> |
