---
title: "方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696aeb619f14a5ebe9a760cbd78a0d0fa876edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="c1c63-102">方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する</span><span class="sxs-lookup"><span data-stu-id="c1c63-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="c1c63-103">次のコード例では、IPv6 のサポートを有効にするようにコンピューター構成ファイルの *machine.config* を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1c63-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="c1c63-104">*machine.config* ファイルは、Windows がインストールされたディレクトリの *%Windir%\Microsoft.NET\Framework* フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c1c63-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="c1c63-105">コンピューターにインストールされた .NET Framework のバージョンごとに、*%Windir%\Microsoft.NET\Framework* の下のフォルダーに別々の *machine.config* ファイルがあります (たとえば、*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*)。</span><span class="sxs-lookup"><span data-stu-id="c1c63-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="c1c63-106">これらの設定は、コンピューター構成ファイルよりも優先されるアプリケーション構成ファイルでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c1c63-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="c1c63-107">.NET Framework バージョン 1.1 以前では、**ipv6 enabled** 構成スイッチの値で <xref:System.Net.Dns?displayProperty=nameWithType> クラスのメンバーが IPv6 アドレスを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1c63-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="c1c63-108">.NET Framework バージョン 2.0 以降では、Windows が IPv6 をサポートしている場合、<xref:System.Net.Dns?displayProperty=nameWithType> クラスのすべてのメンバー (<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> メソッドなど) が 1 つの制限付きで IPv6 アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="c1c63-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="c1c63-109"><xref:System.Net.Dns?displayProperty=nameWithType> クラスの古いメンバー (<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> メソッドなど) は、構成ファイル内の値を読み取り、認識します。</span><span class="sxs-lookup"><span data-stu-id="c1c63-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c63-110">.NET Framework バージョン 2.0 以降では、IPv6 は既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="c1c63-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="c1c63-111">.NET Framework バージョン 1.1 以前では、IPv6 は既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="c1c63-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1c63-112">例</span><span class="sxs-lookup"><span data-stu-id="c1c63-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1c63-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1c63-113">See Also</span></span>  
 [<span data-ttu-id="c1c63-114">IPv6 のアドレス指定</span><span class="sxs-lookup"><span data-stu-id="c1c63-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [<span data-ttu-id="c1c63-115">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c1c63-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="c1c63-116">\<ipv6> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="c1c63-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
