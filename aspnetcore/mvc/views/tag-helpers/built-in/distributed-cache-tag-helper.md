---
title: "分布式缓存标记帮助器 |Microsoft 文档"
author: pkellner
description: "演示如何使用缓存标记帮助器"
ms.author: riande
manager: wpickett
ms.date: 02/14/2017
ms.topic: article
ms.technology: aspnet
ms.prod: aspnet-core
uid: mvc/views/tag-helpers/builtin-th/distributed-cache-tag-helper
ms.openlocfilehash: f5844dade218fdba1169a55fe3ce251a9cc03db2
ms.sourcegitcommit: 3e303620a125325bb9abd4b2d315c106fb8c47fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/19/2018
---
# <a name="distributed-cache-tag-helper"></a>分布式的缓存标记帮助器

作者：[Peter Kellner](http://peterkellner.net) 


分布式缓存标记帮助器提供的功能可以显著提高通过缓存到分布式的缓存源其内容的 ASP.NET Core 应用的性能。

分布式缓存标记帮助器继承自相同的基缓存标记帮助器类。  与缓存标记帮助器关联的所有属性也将都适用于分布式标记帮助器。


分布式缓存标记帮助程序遵循**显式依赖关系原则**称为**构造函数注入**。  具体而言，`IDistributedCache`接口容器传递到分布式缓存标记帮助器的构造函数。  如果没有特定的具体实现`IDistributedCache`已在中创建`ConfigureServices`，通常会在 startup.cs，找到然后分布式缓存标记帮助程序将使用相同的内存中提供程序将缓存的数据存储为基本缓存标记帮助器。

## <a name="distributed-cache-tag-helper-attributes"></a>分布式缓存标记帮助器属性

- - -

### <a name="enabled-expires-on-expires-after-expires-sliding-vary-by-header-vary-by-query-vary-by-route-vary-by-cookie-vary-by-user-vary-by-priority"></a>启用过期上过期之后过期的滑动的标题会有所不同不同的查询不同的路由改变通过 cookie 改变按用户变化依据优先级

有关定义，请参阅缓存标记帮助器。 分布式的缓存标记帮助器继承自与缓存标记帮助器类相同，因此所有这些特性是常见从缓存标记帮助器。

- - -

### <a name="name-required"></a>名称 （必需）

| 特性类型    | 示例值     |
|----------------   |----------------   |
| 字符串    | "my-distributed-cache-unique-key-101"     |

所需`name`属性用作每个实例的分布式缓存标记帮助器存储该缓存的键。  与不同的是基本缓存标记帮助程序为基于 Razor 页名称和位置在 razor 页中的标记帮助程序的每个缓存标记帮助器实例分配一个密钥，分布式缓存标记帮助器仅基于的密钥属性`name`

用法示例：

```cshtml
<distributed-cache name="my-distributed-cache-unique-key-101">
    Time Inside Cache Tag Helper: @DateTime.Now
</distributed-cache>
```

## <a name="distributed-cache-tag-helper-idistributedcache-implementations"></a>分布式缓存标记帮助器 IDistributedCache 实现

有的两个实现`IDistributedCache`内置到 ASP.NET 核心。  一个基于**Sql Server**和其他基于**Redis**。 以下名为"使用分布式缓存"引用的资源处找不到这些实现的详细信息。 这两个实现涉及设置的实例`IDistributedCache`中 ASP.NET Core **startup.cs**。

没有专门与使用的任何特定实现标记特性`IDistributedCache`。



- - -



## <a name="additional-resources"></a>其他资源

* <xref:mvc/views/tag-helpers/builtin-th/cache-tag-helper>
* <xref:fundamentals/dependency-injection#service-lifetimes-and-registration-options>
* <xref:performance/caching/distributed>
* <xref:performance/caching/memory>
* <xref:security/authentication/identity>
