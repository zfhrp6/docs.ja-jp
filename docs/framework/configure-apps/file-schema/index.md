---
title: .NET Framework の構成ファイル スキーマ
ms.custom: ''
ms.date: 05/01/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: 20
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 4af28280de24f3e25362f18985c209b1a2f29523
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="6bc17-102">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="6bc17-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="6bc17-103">構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="6bc17-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="6bc17-104">.NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6bc17-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="6bc17-105">このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。</span><span class="sxs-lookup"><span data-stu-id="6bc17-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="6bc17-106">構成ファイルの種類、形式、および場所については、「[アプリの構成](~/docs/framework/configure-apps/index.md)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bc17-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="6bc17-107">構成ファイルを直接編集する場合は、XML に関する知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="6bc17-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6bc17-108">構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="6bc17-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6bc17-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6bc17-109">In this section</span></span>

<span data-ttu-id="6bc17-110">[**\<configuration>** 要素](~/docs/framework/configure-apps/file-schema/configuration-element.md) すべての構成ファイルの最上位要素である `<configuration>` 要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="6bc17-111">[**\<assemblyBinding>** 要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) 構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="6bc17-112">[**\<linkedConfiguration>** 要素](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) インクルードする構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="6bc17-113">[スタートアップ設定スキーマ](~/docs/framework/configure-apps/file-schema/startup/index.md) 使用する共通言語ランタイムのバージョンを指定する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="6bc17-114">[ランタイム設定スキーマ](~/docs/framework/configure-apps/file-schema/runtime/index.md) アセンブリのバインディングとランタイムの動作を構成する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="6bc17-115">[ネットワーク設定スキーマ](~/docs/framework/configure-apps/file-schema/network/index.md) .NET Framework がインターネットに接続する方法を指定する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="6bc17-116">[暗号設定スキーマ](~/docs/framework/configure-apps/file-schema/cryptography/index.md) アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="6bc17-117">[構成セクション スキーマ](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) カスタム設定の構成セクションを作成し、使用するための要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="6bc17-118">[トレースおよびデバッグ設定のスキーマ](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) トレース スイッチとリスナーを指定する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="6bc17-119">[コンパイラおよび言語プロバイダー設定のスキーマ](~/docs/framework/configure-apps/file-schema/compiler/index.md) 使用できる言語プロバイダーのコンパイラの構成を指定する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="6bc17-120">[アプリケーション設定のスキーマ](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Windows フォームや ASP.NET アプリケーションで、アプリケーション スコープおよびユーザー スコープの設定の格納と取得を可能にする要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="6bc17-121">[アプリ設定スキーマ](~/docs/framework/configure-apps/file-schema/appsettings/index.md) ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bc17-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="6bc17-122">[Web 設定スキーマ](~/docs/framework/configure-apps/file-schema/web/index.md) IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="6bc17-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="6bc17-123">*Aspnet.config* ファイルで使用します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="6bc17-124">[Windows フォーム構成スキーマ](winforms/index.md) マルチ モニターや高 DPI サポートなどのカスタマイズを含む、Windows フォーム アプリケーションの構成セクションのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="6bc17-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="6bc17-125">[WCF 構成スキーマ](~/docs/framework/configure-apps/file-schema/wcf/index.md) WCF サービスとクライアント アプリケーションを構成できるすべての要素。</span><span class="sxs-lookup"><span data-stu-id="6bc17-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="6bc17-126">[WCF ディレクティブ構文](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) .svc コンパイラによって使用されるページ固有の属性を定義する、`@ServiceHost` ディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="6bc17-127">[WIF 構成スキーマ](windows-identity-foundation/index.md) Windows Identity Foundation (WIF) 構成スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="6bc17-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6bc17-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bc17-128">Related sections</span></span>

<span data-ttu-id="6bc17-129">[リモート処理設定スキーマ](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-129">[Remoting Settings Schema](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="6bc17-130">[ASP.NET の設定スキーマ](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) ASP.NET Web アプリケーションの動作を制御する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-130">[ASP.NET Settings Schema](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="6bc17-131">[Web サービス設定スキーマ](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-131">[Web Services Settings Schema](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="6bc17-132">[.NET Framework アプリの構成](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bc17-132">[Configuring .NET Framework Apps](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
