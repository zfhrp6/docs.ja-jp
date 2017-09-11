---
title: "Windows フォームの構成セクション | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: 39e8e757a446b30ab18914465853138e1c239e40
ms.openlocfilehash: dedf9497a684c4b11f84b60de21ec73b563c6d19
ms.contentlocale: ja-jp
ms.lasthandoff: 05/03/2017

---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="76fa6-102">Windows フォームの構成セクション</span><span class="sxs-lookup"><span data-stu-id="76fa6-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="76fa6-103">Windows フォームの構成設定により、カスタマイズされたアプリケーション設定に関する情報 (マルチ モニターや高 DPI のサポート、その他の定義済みの構成設定など) を Windows フォームのアプリで格納したり、取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="76fa6-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="76fa6-104">Windows フォームのアプリケーション構成設定は、アプリケーション構成ファイルの `System.Windows.Forms.ConfigurationSection` 要素に格納されます。</span><span class="sxs-lookup"><span data-stu-id="76fa6-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="76fa6-105">構文</span><span class="sxs-lookup"><span data-stu-id="76fa6-105">Syntax</span></span>

```xml
<configuration>
  \<System.Windows.Forms.ConfigurationSection>
  ...
  \</System.Windows.Forms.ConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76fa6-106">属性と要素</span><span class="sxs-lookup"><span data-stu-id="76fa6-106">Attributes and elements</span></span>

<span data-ttu-id="76fa6-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="76fa6-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="76fa6-108">属性</span><span class="sxs-lookup"><span data-stu-id="76fa6-108">Attributes</span></span>

<span data-ttu-id="76fa6-109">なし。</span><span class="sxs-lookup"><span data-stu-id="76fa6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76fa6-110">子要素</span><span class="sxs-lookup"><span data-stu-id="76fa6-110">Child elements</span></span>

<span data-ttu-id="76fa6-111">要素</span><span class="sxs-lookup"><span data-stu-id="76fa6-111">Element</span></span>  |<span data-ttu-id="76fa6-112">説明</span><span class="sxs-lookup"><span data-stu-id="76fa6-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="76fa6-113">指定した値を持つ構成設定キーを追加します</span><span class="sxs-lookup"><span data-stu-id="76fa6-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="76fa6-114">親要素</span><span class="sxs-lookup"><span data-stu-id="76fa6-114">Parent elements</span></span>

<span data-ttu-id="76fa6-115">要素</span><span class="sxs-lookup"><span data-stu-id="76fa6-115">Element</span></span>  |<span data-ttu-id="76fa6-116">説明</span><span class="sxs-lookup"><span data-stu-id="76fa6-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="76fa6-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="76fa6-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="76fa6-118">共通言語ランタイムと Windows フォームのアプリケーションで使用されるすべての構成ファイルのルート要素です</span><span class="sxs-lookup"><span data-stu-id="76fa6-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="76fa6-119">コメント</span><span class="sxs-lookup"><span data-stu-id="76fa6-119">Remarks</span></span>

<span data-ttu-id="76fa6-120">.NET Framework 4.7 を使用すれば、.NET Framework の最近のリリースで追加された機能が利用できる Windows フォームのアプリケーションを、`<System.Windows.Forms.ConfigurationSection>` 要素で構成できます。</span><span class="sxs-lookup"><span data-stu-id="76fa6-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="76fa6-121">`<System.Windows.Forms.ConfigurationSection>` 要素には 1 つまたは複数の子の [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) 要素を含めることができ、各要素には特定の構成設定が定義されます。</span><span class="sxs-lookup"><span data-stu-id="76fa6-121">The `<System.Windows.Forms.ConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="76fa6-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="76fa6-122">See also</span></span>

<span data-ttu-id="76fa6-123">[構成ファイル スキーマ](../index.md)
[Windows フォームでの高 DPI サポート](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="76fa6-123">[Configuration File Schema](../index.md)
[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)</span></span>

