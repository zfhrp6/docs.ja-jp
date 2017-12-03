---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaec1b7d179810faaba016cfa0c5eb7e6c950ab6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="38c0e-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="38c0e-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="38c0e-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="38c0e-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c0e-104">構文</span><span class="sxs-lookup"><span data-stu-id="38c0e-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="38c0e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="38c0e-105">Methods</span></span>  
 <span data-ttu-id="38c0e-106">TcpConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="38c0e-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="38c0e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="38c0e-107">Properties</span></span>  
 <span data-ttu-id="38c0e-108">TcpConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="38c0e-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="38c0e-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="38c0e-109">GroupName</span></span>  
 <span data-ttu-id="38c0e-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="38c0e-110">Data type: string</span></span>  
  
 <span data-ttu-id="38c0e-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38c0e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38c0e-112">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="38c0e-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="38c0e-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="38c0e-113">IdleTimeout</span></span>  
 <span data-ttu-id="38c0e-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="38c0e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="38c0e-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38c0e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38c0e-116">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="38c0e-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="38c0e-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="38c0e-117">LeaseTimeout</span></span>  
 <span data-ttu-id="38c0e-118">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="38c0e-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="38c0e-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38c0e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38c0e-120">リース操作を完了する必要がある、タイムアウトまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="38c0e-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="38c0e-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="38c0e-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="38c0e-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="38c0e-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="38c0e-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="38c0e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38c0e-124">各エンドポイントの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="38c0e-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38c0e-125">要件</span><span class="sxs-lookup"><span data-stu-id="38c0e-125">Requirements</span></span>  
  
|<span data-ttu-id="38c0e-126">MOF</span><span class="sxs-lookup"><span data-stu-id="38c0e-126">MOF</span></span>|<span data-ttu-id="38c0e-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="38c0e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="38c0e-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="38c0e-128">Namespace</span></span>|<span data-ttu-id="38c0e-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="38c0e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38c0e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="38c0e-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
