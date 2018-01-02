---
title: "&lt;アサート&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9670cf0faa3e7f69b8f99b09fa26741991a60481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltassertgt-element"></a><span data-ttu-id="347dc-102">&lt;アサート&gt;要素</span><span class="sxs-lookup"><span data-stu-id="347dc-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="347dc-103"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。</span><span class="sxs-lookup"><span data-stu-id="347dc-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="347dc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="347dc-104">\<configuration></span></span>  
<span data-ttu-id="347dc-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="347dc-105">\<system.diagnostics></span></span>  
<span data-ttu-id="347dc-106">\<アサート ></span><span class="sxs-lookup"><span data-stu-id="347dc-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347dc-107">構文</span><span class="sxs-lookup"><span data-stu-id="347dc-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="347dc-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="347dc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="347dc-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="347dc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="347dc-110">属性</span><span class="sxs-lookup"><span data-stu-id="347dc-110">Attributes</span></span>  
  
|<span data-ttu-id="347dc-111">属性</span><span class="sxs-lookup"><span data-stu-id="347dc-111">Attribute</span></span>|<span data-ttu-id="347dc-112">説明</span><span class="sxs-lookup"><span data-stu-id="347dc-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="347dc-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="347dc-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="347dc-114">かどうかを表示する際にメッセージ ボックスを指定します、 **Debug.Assert**メソッドを評価する**false**です。</span><span class="sxs-lookup"><span data-stu-id="347dc-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="347dc-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="347dc-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="347dc-116">場合に、メッセージを書き込むファイルの名前を指定**Debug.Assert**に評価される**false**です。</span><span class="sxs-lookup"><span data-stu-id="347dc-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="347dc-117">assertuienabled 属性</span><span class="sxs-lookup"><span data-stu-id="347dc-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="347dc-118">値</span><span class="sxs-lookup"><span data-stu-id="347dc-118">Value</span></span>|<span data-ttu-id="347dc-119">説明</span><span class="sxs-lookup"><span data-stu-id="347dc-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="347dc-120">メッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="347dc-120">Displays the message box.</span></span> <span data-ttu-id="347dc-121">既定値です。</span><span class="sxs-lookup"><span data-stu-id="347dc-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="347dc-122">メッセージ ボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="347dc-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="347dc-123">子要素</span><span class="sxs-lookup"><span data-stu-id="347dc-123">Child Elements</span></span>  
 <span data-ttu-id="347dc-124">なし。</span><span class="sxs-lookup"><span data-stu-id="347dc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="347dc-125">親要素</span><span class="sxs-lookup"><span data-stu-id="347dc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="347dc-126">要素</span><span class="sxs-lookup"><span data-stu-id="347dc-126">Element</span></span>|<span data-ttu-id="347dc-127">説明</span><span class="sxs-lookup"><span data-stu-id="347dc-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="347dc-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="347dc-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="347dc-129">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="347dc-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="347dc-130">コメント</span><span class="sxs-lookup"><span data-stu-id="347dc-130">Remarks</span></span>  
 <span data-ttu-id="347dc-131">両方の属性で、 **\<アサート >**要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="347dc-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="347dc-132">メッセージを書き込むファイルを指定せずメッセージ ボックスを無効にできますか、メッセージ ボックスが有効なのままにしてメッセージを書き込むファイルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="347dc-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="347dc-133">例</span><span class="sxs-lookup"><span data-stu-id="347dc-133">Example</span></span>  
 <span data-ttu-id="347dc-134">次の例を呼び出すときに表示するメッセージ ボックスを無効にする方法を示しています。 **Debug.Assert**にメッセージを書き込むと`c:\log.txt`です。</span><span class="sxs-lookup"><span data-stu-id="347dc-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="347dc-135">参照</span><span class="sxs-lookup"><span data-stu-id="347dc-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="347dc-136">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="347dc-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
