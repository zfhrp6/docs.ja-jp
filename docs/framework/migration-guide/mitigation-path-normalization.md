---
title: "軽減策: パスの正規化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edae357dad95a363926afbacc8e52355a1bcbd65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="835d1-102">軽減策: パスの正規化</span><span class="sxs-lookup"><span data-stu-id="835d1-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="835d1-103">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、.NET Framework のパスの正規化が変更されました。</span><span class="sxs-lookup"><span data-stu-id="835d1-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="835d1-104">パスの正規化とは</span><span class="sxs-lookup"><span data-stu-id="835d1-104">What is path normalization?</span></span>  
 <span data-ttu-id="835d1-105">パスの正規化では、パスまたはファイルを識別する文字列を変更し、対象のオペレーティング システムの有効なパスに準拠するようにします。</span><span class="sxs-lookup"><span data-stu-id="835d1-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="835d1-106">通常、正規化では次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="835d1-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="835d1-107">コンポーネントとディレクトリの区切り記号を正規化する。</span><span class="sxs-lookup"><span data-stu-id="835d1-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="835d1-108">現在のディレクトリを相対パスに適用する。</span><span class="sxs-lookup"><span data-stu-id="835d1-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="835d1-109">パスの相対ディレクトリ (`.`) または親ディレクトリ (`..`) を評価する。</span><span class="sxs-lookup"><span data-stu-id="835d1-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="835d1-110">指定した文字をトリミングする。</span><span class="sxs-lookup"><span data-stu-id="835d1-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="835d1-111">変更点</span><span class="sxs-lookup"><span data-stu-id="835d1-111">The changes</span></span>  
 <span data-ttu-id="835d1-112">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、次のようにパスの正規化が変更されました。</span><span class="sxs-lookup"><span data-stu-id="835d1-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="835d1-113">ランタイムはオペレーティング システムの [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) 関数に従って、パスを正規化します。</span><span class="sxs-lookup"><span data-stu-id="835d1-113">The runtime defers to the operating system's [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="835d1-114">正規化では、ディレクトリ セグメントの末尾 (ディレクトリ名の末尾のスペースなど) がトリミングされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="835d1-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="835d1-115">`\\.\` や `\\?\` (mscorlib.dll のファイル I/O API の場合) を含む、完全に信頼できるデバイス パス構文がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="835d1-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="835d1-116">ランタイムではデバイス構文パスは検証されません。</span><span class="sxs-lookup"><span data-stu-id="835d1-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="835d1-117">代替データ ストリームにアクセスするためのデバイス構文の使用はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="835d1-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="835d1-118">影響</span><span class="sxs-lookup"><span data-stu-id="835d1-118">Impact</span></span>  
 <span data-ttu-id="835d1-119">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降を対象とするアプリでは、これらの変更は既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="835d1-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="835d1-120">パフォーマンスが向上すると同時に、以前はアクセス不可だったパスにメソッドでアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="835d1-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="835d1-121">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前のバージョンを対象とするアプリが [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降で実行される場合、この変更の影響は受けません。</span><span class="sxs-lookup"><span data-stu-id="835d1-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="835d1-122">軽減策</span><span class="sxs-lookup"><span data-stu-id="835d1-122">Mitigation</span></span>  
 <span data-ttu-id="835d1-123">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降を対象とするアプリでこの変更を無効にし、従来の正規化を使用することができます。その場合、アプリケーション構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="835d1-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="835d1-124">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前を対象とするものの、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降で実行されているアプリは、パスの正規化の変更を有効にすることができます。その場合、アプリケーション構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="835d1-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="835d1-125">参照</span><span class="sxs-lookup"><span data-stu-id="835d1-125">See Also</span></span>  
 [<span data-ttu-id="835d1-126">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="835d1-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
