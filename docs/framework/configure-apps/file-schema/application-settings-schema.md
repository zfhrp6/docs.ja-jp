---
title: アプリケーション設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7af6342e9c05fc4e6c1bf4daac59db14ccdf22c7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741738"
---
# <a name="application-settings-schema"></a><span data-ttu-id="39639-102">アプリケーション設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="39639-102">Application Settings schema</span></span>

<span data-ttu-id="39639-103">アプリケーションの設定を保存し、アプリケーション スコープ設定し、ユーザー スコープ設定を取得する Windows フォームまたは ASP.NET アプリケーションを許可します。</span><span class="sxs-lookup"><span data-stu-id="39639-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="39639-104">このコンテキストで、*設定*のアプリケーション固有または現在のユーザーに特定できる情報は、-ユーザーにデータベース接続文字列から何かの既定のウィンドウ サイズを優先します。</span><span class="sxs-lookup"><span data-stu-id="39639-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="39639-105">既定では、Windows フォーム アプリケーションにおけるアプリケーションの設定を使用して、<xref:System.Configuration.LocalFileSettingsProvider>クラスは、.NET 構成システムを使用して、XML 構成ファイルに設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="39639-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="39639-106">アプリケーションの設定で使用されるファイルの詳細については、次を参照してください。[アプリケーション設定アーキテクチャ](~/docs/framework/winforms/advanced/application-settings-architecture.md)です。</span><span class="sxs-lookup"><span data-stu-id="39639-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="39639-107">アプリケーションの設定は、使用して、構成ファイルの一部として、次の要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="39639-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="39639-108">要素</span><span class="sxs-lookup"><span data-stu-id="39639-108">Element</span></span>                    | <span data-ttu-id="39639-109">説明</span><span class="sxs-lookup"><span data-stu-id="39639-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="39639-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="39639-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="39639-111">すべてを含む**\<設定 >** タグはアプリケーションに固有です。</span><span class="sxs-lookup"><span data-stu-id="39639-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="39639-112">**\<ユーザー >**</span><span class="sxs-lookup"><span data-stu-id="39639-112">**\<userSettings>**</span></span>        | <span data-ttu-id="39639-113">すべてが含まれます**\<設定 >** タグは、現在のユーザーを特定します。</span><span class="sxs-lookup"><span data-stu-id="39639-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="39639-114">**\<設定 >**</span><span class="sxs-lookup"><span data-stu-id="39639-114">**\<setting>**</span></span>             | <span data-ttu-id="39639-115">設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="39639-115">Defines a setting.</span></span> <span data-ttu-id="39639-116">いずれかの子 **\<applicationSettings >** または**\<ユーザー >** です。</span><span class="sxs-lookup"><span data-stu-id="39639-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="39639-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="39639-117">**\<value>**</span></span>               | <span data-ttu-id="39639-118">設定の値を定義します。</span><span class="sxs-lookup"><span data-stu-id="39639-118">Defines a setting's value.</span></span> <span data-ttu-id="39639-119">子**\<設定 >** です。</span><span class="sxs-lookup"><span data-stu-id="39639-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="39639-120">\<applicationSettings > 要素</span><span class="sxs-lookup"><span data-stu-id="39639-120">\<applicationSettings> element</span></span>

<span data-ttu-id="39639-121">この要素には、すべてが含まれています**\<設定 >** タグは、クライアント コンピューターにアプリケーションのインスタンスに固有です。</span><span class="sxs-lookup"><span data-stu-id="39639-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="39639-122">属性は定義されません。</span><span class="sxs-lookup"><span data-stu-id="39639-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="39639-123">\<ユーザー > 要素</span><span class="sxs-lookup"><span data-stu-id="39639-123">\<userSettings> element</span></span>

<span data-ttu-id="39639-124">この要素には、すべてが含まれています**\<設定 >** アプリケーションが現在使用しているユーザーに固有のタグ。</span><span class="sxs-lookup"><span data-stu-id="39639-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="39639-125">属性は定義されません。</span><span class="sxs-lookup"><span data-stu-id="39639-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="39639-126">\<設定 > 要素</span><span class="sxs-lookup"><span data-stu-id="39639-126">\<setting> element</span></span>

<span data-ttu-id="39639-127">この要素は、設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="39639-127">This element defines a setting.</span></span> <span data-ttu-id="39639-128">次の属性があります。</span><span class="sxs-lookup"><span data-stu-id="39639-128">It has the following attributes.</span></span>

| <span data-ttu-id="39639-129">属性</span><span class="sxs-lookup"><span data-stu-id="39639-129">Attribute</span></span>        | <span data-ttu-id="39639-130">説明</span><span class="sxs-lookup"><span data-stu-id="39639-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="39639-131">**name**</span><span class="sxs-lookup"><span data-stu-id="39639-131">**name**</span></span>         | <span data-ttu-id="39639-132">必須。</span><span class="sxs-lookup"><span data-stu-id="39639-132">Required.</span></span> <span data-ttu-id="39639-133">設定の一意の ID。</span><span class="sxs-lookup"><span data-stu-id="39639-133">The unique ID of the setting.</span></span> <span data-ttu-id="39639-134">Visual Studio で作成した設定は、名前で保存`ProjectName.Properties.Settings`です。</span><span class="sxs-lookup"><span data-stu-id="39639-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="39639-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="39639-135">**serializedAs**</span></span> | <span data-ttu-id="39639-136">必須。</span><span class="sxs-lookup"><span data-stu-id="39639-136">Required.</span></span> <span data-ttu-id="39639-137">テキスト値をシリアル化するために使用する形式。</span><span class="sxs-lookup"><span data-stu-id="39639-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="39639-138">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39639-138">Valid values are:</span></span><br><br><span data-ttu-id="39639-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="39639-139">- `string`.</span></span> <span data-ttu-id="39639-140">使用して文字列として値がシリアル化、<xref:System.ComponentModel.TypeConverter>です。</span><span class="sxs-lookup"><span data-stu-id="39639-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="39639-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="39639-141">- `xml`.</span></span> <span data-ttu-id="39639-142">XML シリアル化を使用して、値がシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="39639-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="39639-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="39639-143">- `binary`.</span></span> <span data-ttu-id="39639-144">値は、バイナリのシリアル化を使用して、テキスト エンコードされたバイナリとしてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="39639-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="39639-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="39639-145">- `custom`.</span></span> <span data-ttu-id="39639-146">設定プロバイダーは、この設定の固有の情報しシリアル化し、逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="39639-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="39639-147">\<値 > 要素</span><span class="sxs-lookup"><span data-stu-id="39639-147">\<value> element</span></span>

<span data-ttu-id="39639-148">この要素には、設定の値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39639-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="39639-149">例</span><span class="sxs-lookup"><span data-stu-id="39639-149">Example</span></span>

<span data-ttu-id="39639-150">次の例では、2 つのアプリケーション スコープ設定と 2 つのユーザー スコープ設定を定義するアプリケーションの設定ファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="39639-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="39639-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="39639-151">See also</span></span>

<span data-ttu-id="39639-152">[アプリケーション設定の概要](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="39639-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="39639-153">アプリケーション設定アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="39639-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
