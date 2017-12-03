---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18740c4c87aaeafcd0a28991376e0c45fe688223
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="579f7-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="579f7-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="579f7-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="579f7-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="579f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="579f7-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="579f7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="579f7-105">Methods</span></span>  
 <span data-ttu-id="579f7-106">NamedPipeConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="579f7-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="579f7-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="579f7-107">Properties</span></span>  
 <span data-ttu-id="579f7-108">NamedPipeConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="579f7-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="579f7-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="579f7-109">GroupName</span></span>  
 <span data-ttu-id="579f7-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="579f7-110">Data type: string</span></span>  
  
 <span data-ttu-id="579f7-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="579f7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="579f7-112">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="579f7-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="579f7-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="579f7-113">IdleTimeout</span></span>  
 <span data-ttu-id="579f7-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="579f7-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="579f7-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="579f7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="579f7-116">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="579f7-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="579f7-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="579f7-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="579f7-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="579f7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="579f7-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="579f7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="579f7-120">クライアント上の各エンドポイントでの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="579f7-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="579f7-121">要件</span><span class="sxs-lookup"><span data-stu-id="579f7-121">Requirements</span></span>  
  
|<span data-ttu-id="579f7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="579f7-122">MOF</span></span>|<span data-ttu-id="579f7-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="579f7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="579f7-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="579f7-124">Namespace</span></span>|<span data-ttu-id="579f7-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="579f7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="579f7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="579f7-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
