<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f00defb149ee1ac4a799e44a9783c7fc",
  "translation_date": "2025-06-06T18:37:16+00:00",
  "source_file": "01-CoreConcepts/README.md",
  "language_code": "vi"
}
-->
# 📖 Khái niệm cốt lõi MCP: Làm chủ Model Context Protocol cho tích hợp AI

Model Context Protocol (MCP) là một khuôn khổ tiêu chuẩn mạnh mẽ giúp tối ưu hóa giao tiếp giữa các Large Language Models (LLMs) và các công cụ, ứng dụng, nguồn dữ liệu bên ngoài. Hướng dẫn tối ưu hóa SEO này sẽ đưa bạn qua các khái niệm cốt lõi của MCP, đảm bảo bạn hiểu kiến trúc client-server, các thành phần thiết yếu, cơ chế giao tiếp và các thực hành tốt nhất khi triển khai.

## Tổng quan

Bài học này khám phá kiến trúc cơ bản và các thành phần tạo nên hệ sinh thái Model Context Protocol (MCP). Bạn sẽ tìm hiểu về kiến trúc client-server, các thành phần chính và cơ chế giao tiếp vận hành các tương tác MCP.

## 👩‍🎓 Mục tiêu học tập chính

Sau bài học này, bạn sẽ:

- Hiểu kiến trúc client-server của MCP.
- Xác định vai trò và trách nhiệm của Hosts, Clients và Servers.
- Phân tích các tính năng cốt lõi giúp MCP trở thành lớp tích hợp linh hoạt.
- Tìm hiểu cách thông tin lưu chuyển trong hệ sinh thái MCP.
- Thu thập kiến thức thực tiễn qua các ví dụ mã trong .NET, Java, Python và JavaScript.

## 🔎 Kiến trúc MCP: Cái nhìn sâu hơn

Hệ sinh thái MCP được xây dựng trên mô hình client-server. Cấu trúc mô-đun này cho phép các ứng dụng AI tương tác hiệu quả với công cụ, cơ sở dữ liệu, API và tài nguyên ngữ cảnh. Hãy cùng phân tích kiến trúc này qua các thành phần chính.

### 1. Hosts

Trong Model Context Protocol (MCP), Hosts đóng vai trò quan trọng như giao diện chính mà người dùng tương tác với protocol. Hosts là các ứng dụng hoặc môi trường khởi tạo kết nối với MCP servers để truy cập dữ liệu, công cụ và prompts. Ví dụ về Hosts bao gồm các môi trường phát triển tích hợp (IDEs) như Visual Studio Code, công cụ AI như Claude Desktop, hoặc các agent tùy chỉnh cho các nhiệm vụ cụ thể.

**Hosts** là các ứng dụng LLM khởi tạo kết nối. Họ:

- Thực thi hoặc tương tác với các mô hình AI để tạo ra phản hồi.
- Khởi tạo kết nối với MCP servers.
- Quản lý luồng hội thoại và giao diện người dùng.
- Kiểm soát quyền hạn và các ràng buộc bảo mật.
- Xử lý sự đồng ý của người dùng cho việc chia sẻ dữ liệu và thực thi công cụ.

### 2. Clients

Clients là các thành phần thiết yếu giúp tạo điều kiện cho tương tác giữa Hosts và MCP servers. Clients hoạt động như cầu nối, cho phép Hosts truy cập và sử dụng các chức năng do MCP servers cung cấp. Họ đóng vai trò quan trọng trong việc đảm bảo giao tiếp mượt mà và trao đổi dữ liệu hiệu quả trong kiến trúc MCP.

**Clients** là các connector bên trong ứng dụng host. Họ:

- Gửi yêu cầu đến servers kèm theo prompts/hướng dẫn.
- Đàm phán khả năng với servers.
- Quản lý các yêu cầu thực thi công cụ từ mô hình.
- Xử lý và hiển thị phản hồi cho người dùng.

### 3. Servers

Servers chịu trách nhiệm xử lý các yêu cầu từ MCP clients và cung cấp phản hồi phù hợp. Họ quản lý các hoạt động như truy xuất dữ liệu, thực thi công cụ và tạo prompt. Servers đảm bảo giao tiếp giữa clients và Hosts hiệu quả, đáng tin cậy, duy trì tính toàn vẹn của quá trình tương tác.

**Servers** là các dịch vụ cung cấp ngữ cảnh và khả năng. Họ:

- Đăng ký các tính năng sẵn có (tài nguyên, prompt, công cụ)
- Nhận và thực thi các cuộc gọi công cụ từ client
- Cung cấp thông tin ngữ cảnh để nâng cao phản hồi của mô hình
- Trả kết quả về cho client
- Duy trì trạng thái qua các tương tác khi cần

Servers có thể được phát triển bởi bất kỳ ai để mở rộng khả năng mô hình với chức năng chuyên biệt.

### 4. Tính năng Server

Servers trong Model Context Protocol (MCP) cung cấp các khối xây dựng cơ bản cho phép tương tác phong phú giữa clients, hosts và các mô hình ngôn ngữ. Các tính năng này được thiết kế để nâng cao khả năng của MCP bằng cách cung cấp ngữ cảnh có cấu trúc, công cụ và prompt.

MCP servers có thể cung cấp bất kỳ tính năng nào sau đây:

#### 📑 Tài nguyên

Tài nguyên trong Model Context Protocol (MCP) bao gồm nhiều loại ngữ cảnh và dữ liệu có thể được người dùng hoặc mô hình AI sử dụng. Bao gồm:

- **Dữ liệu ngữ cảnh**: Thông tin và ngữ cảnh mà người dùng hoặc mô hình AI có thể tận dụng để ra quyết định và thực hiện nhiệm vụ.
- **Cơ sở tri thức và kho tài liệu**: Tập hợp dữ liệu có cấu trúc và không có cấu trúc, như bài viết, tài liệu hướng dẫn, và bài nghiên cứu, cung cấp thông tin và kiến thức giá trị.
- **Tệp và cơ sở dữ liệu cục bộ**: Dữ liệu lưu trữ tại thiết bị hoặc trong cơ sở dữ liệu, có thể truy cập để xử lý và phân tích.
- **API và dịch vụ web**: Giao diện và dịch vụ bên ngoài cung cấp thêm dữ liệu và chức năng, cho phép tích hợp với các nguồn tài nguyên và công cụ trực tuyến.

Một ví dụ về tài nguyên có thể là sơ đồ cơ sở dữ liệu hoặc tệp có thể truy cập như sau:

```text
file://log.txt
database://schema
```

### 🤖 Prompts

Prompts trong Model Context Protocol (MCP) bao gồm nhiều mẫu định sẵn và các mẫu tương tác được thiết kế để đơn giản hóa quy trình làm việc của người dùng và nâng cao giao tiếp. Bao gồm:

- **Thông điệp và quy trình làm việc theo mẫu**: Các thông điệp và quy trình đã được cấu trúc sẵn giúp hướng dẫn người dùng qua các nhiệm vụ và tương tác cụ thể.
- **Mẫu tương tác định sẵn**: Chuỗi hành động và phản hồi tiêu chuẩn giúp giao tiếp nhất quán và hiệu quả.
- **Mẫu hội thoại chuyên biệt**: Các mẫu tùy chỉnh dành cho các loại hội thoại cụ thể, đảm bảo các tương tác phù hợp và có ngữ cảnh.

Một mẫu prompt có thể trông như sau:

```markdown
Generate a product slogan based on the following {{product}} with the following {{keywords}}
```

#### ⛏️ Công cụ

Công cụ trong Model Context Protocol (MCP) là các hàm mà mô hình AI có thể thực thi để thực hiện các nhiệm vụ cụ thể. Những công cụ này được thiết kế để nâng cao khả năng của mô hình AI bằng cách cung cấp các thao tác có cấu trúc và đáng tin cậy. Các điểm chính bao gồm:

- **Hàm để mô hình AI thực thi**: Công cụ là các hàm có thể gọi để thực hiện nhiều nhiệm vụ khác nhau.
- **Tên và mô tả riêng biệt**: Mỗi công cụ có tên duy nhất và mô tả chi tiết giải thích mục đích và chức năng.
- **Tham số và đầu ra**: Công cụ nhận các tham số cụ thể và trả về kết quả có cấu trúc, đảm bảo kết quả nhất quán và dự đoán được.
- **Hàm riêng biệt**: Công cụ thực hiện các chức năng riêng biệt như tìm kiếm web, tính toán, truy vấn cơ sở dữ liệu.

Một ví dụ về công cụ có thể như sau:

```typescript
server.tool(
  "GetProducts",
  {
    pageSize: z.string().optional(),
    pageCount: z.string().optional()
  }, () => {
    // return results from API
  }
)
```

## Tính năng Client

Trong Model Context Protocol (MCP), clients cung cấp một số tính năng chính cho servers, nâng cao chức năng và tương tác trong protocol. Một trong các tính năng nổi bật là Sampling.

### 👉 Sampling

- **Hành vi agentic do server khởi xướng**: Clients cho phép servers khởi xướng các hành động hoặc hành vi cụ thể một cách tự động, nâng cao khả năng động của hệ thống.
- **Tương tác đệ quy với LLM**: Tính năng này cho phép tương tác đệ quy với các mô hình ngôn ngữ lớn (LLMs), hỗ trợ xử lý nhiệm vụ phức tạp và lặp đi lặp lại.
- **Yêu cầu bổ sung kết quả mô hình**: Servers có thể yêu cầu thêm các kết quả từ mô hình, đảm bảo phản hồi đầy đủ và phù hợp với ngữ cảnh.

## Luồng thông tin trong MCP

Model Context Protocol (MCP) định nghĩa luồng thông tin có cấu trúc giữa hosts, clients, servers và các mô hình. Hiểu luồng này giúp làm rõ cách các yêu cầu của người dùng được xử lý và cách công cụ bên ngoài cùng dữ liệu được tích hợp vào phản hồi mô hình.

- **Host khởi tạo kết nối**  
  Ứng dụng host (ví dụ IDE hoặc giao diện chat) thiết lập kết nối đến MCP server, thường qua STDIO, WebSocket hoặc phương thức truyền tải được hỗ trợ khác.

- **Đàm phán khả năng**  
  Client (nhúng trong host) và server trao đổi thông tin về các tính năng, công cụ, tài nguyên và phiên bản protocol mà họ hỗ trợ. Điều này đảm bảo cả hai bên hiểu khả năng có sẵn cho phiên làm việc.

- **Yêu cầu người dùng**  
  Người dùng tương tác với host (ví dụ nhập prompt hoặc lệnh). Host thu thập đầu vào này và chuyển cho client xử lý.

- **Sử dụng tài nguyên hoặc công cụ**  
  - Client có thể yêu cầu thêm ngữ cảnh hoặc tài nguyên từ server (như tệp, mục cơ sở dữ liệu hoặc bài viết trong kho tri thức) để làm phong phú hiểu biết của mô hình.
  - Nếu mô hình xác định cần công cụ (ví dụ lấy dữ liệu, tính toán, gọi API), client gửi yêu cầu gọi công cụ tới server, chỉ định tên công cụ và tham số.

- **Thực thi trên server**  
  Server nhận yêu cầu tài nguyên hoặc công cụ, thực hiện các thao tác cần thiết (chạy hàm, truy vấn cơ sở dữ liệu, lấy tệp), và trả kết quả về client dưới định dạng có cấu trúc.

- **Tạo phản hồi**  
  Client tích hợp phản hồi từ server (dữ liệu tài nguyên, kết quả công cụ, v.v.) vào tương tác mô hình đang diễn ra. Mô hình sử dụng thông tin này để tạo ra phản hồi đầy đủ và phù hợp ngữ cảnh.

- **Hiển thị kết quả**  
  Host nhận kết quả cuối cùng từ client và hiển thị cho người dùng, thường bao gồm cả văn bản do mô hình tạo ra và kết quả từ các công cụ hoặc tài nguyên.

Luồng này giúp MCP hỗ trợ các ứng dụng AI tiên tiến, tương tác và nhận biết ngữ cảnh bằng cách kết nối liền mạch mô hình với các công cụ và nguồn dữ liệu bên ngoài.

## Chi tiết Protocol

MCP (Model Context Protocol) được xây dựng trên [JSON-RPC 2.0](https://www.jsonrpc.org/), cung cấp định dạng thông điệp tiêu chuẩn, ngôn ngữ-độc lập cho giao tiếp giữa hosts, clients và servers. Nền tảng này cho phép tương tác đáng tin cậy, có cấu trúc và mở rộng trên nhiều nền tảng và ngôn ngữ lập trình khác nhau.

### Các tính năng chính của Protocol

MCP mở rộng JSON-RPC 2.0 với các quy ước bổ sung cho việc gọi công cụ, truy cập tài nguyên và quản lý prompt. Nó hỗ trợ nhiều lớp truyền tải (STDIO, WebSocket, SSE) và cho phép giao tiếp an toàn, mở rộng và ngôn ngữ-độc lập giữa các thành phần.

#### 🧢 Protocol cơ bản

- **Định dạng thông điệp JSON-RPC**: Tất cả yêu cầu và phản hồi sử dụng chuẩn JSON-RPC 2.0, đảm bảo cấu trúc nhất quán cho các cuộc gọi phương thức, tham số, kết quả và xử lý lỗi.
- **Kết nối trạng thái**: Phiên MCP duy trì trạng thái qua nhiều yêu cầu, hỗ trợ hội thoại liên tục, tích lũy ngữ cảnh và quản lý tài nguyên.
- **Đàm phán khả năng**: Trong quá trình thiết lập kết nối, clients và servers trao đổi thông tin về các tính năng hỗ trợ, phiên bản protocol, công cụ và tài nguyên có sẵn. Điều này đảm bảo cả hai bên hiểu khả năng của nhau và có thể điều chỉnh phù hợp.

#### ➕ Tiện ích bổ sung

Dưới đây là một số tiện ích và mở rộng protocol mà MCP cung cấp để nâng cao trải nghiệm nhà phát triển và hỗ trợ các kịch bản nâng cao:

- **Tùy chọn cấu hình**: MCP cho phép cấu hình động các tham số phiên làm việc, như quyền công cụ, truy cập tài nguyên và cài đặt mô hình, tùy chỉnh theo từng tương tác.
- **Theo dõi tiến trình**: Các thao tác kéo dài có thể báo cáo cập nhật tiến độ, giúp giao diện người dùng phản hồi nhanh và trải nghiệm tốt hơn khi thực hiện các nhiệm vụ phức tạp.
- **Hủy yêu cầu**: Clients có thể hủy các yêu cầu đang thực hiện, cho phép người dùng ngắt các thao tác không còn cần thiết hoặc tốn quá nhiều thời gian.
- **Báo cáo lỗi**: Thông điệp lỗi và mã lỗi chuẩn hóa giúp chẩn đoán sự cố, xử lý thất bại một cách trơn tru và cung cấp phản hồi có thể hành động cho người dùng và nhà phát triển.
- **Ghi log**: Cả clients và servers có thể phát ra log có cấu trúc để kiểm toán, gỡ lỗi và giám sát tương tác protocol.

Bằng cách tận dụng các tính năng protocol này, MCP đảm bảo giao tiếp mạnh mẽ, an toàn và linh hoạt giữa các mô hình ngôn ngữ và công cụ hoặc nguồn dữ liệu bên ngoài.

### 🔐 Các cân nhắc về bảo mật

Các triển khai MCP cần tuân thủ một số nguyên tắc bảo mật chính để đảm bảo tương tác an toàn và đáng tin cậy:

- **Sự đồng ý và kiểm soát của người dùng**: Người dùng phải cung cấp sự đồng ý rõ ràng trước khi bất kỳ dữ liệu nào được truy cập hoặc thao tác được thực hiện. Họ cần có kiểm soát rõ ràng về dữ liệu nào được chia sẻ và hành động nào được ủy quyền, được hỗ trợ bởi giao diện người dùng trực quan để xem xét và phê duyệt hoạt động.

- **Bảo mật dữ liệu**: Dữ liệu người dùng chỉ được tiết lộ khi có sự đồng ý rõ ràng và phải được bảo vệ bằng các kiểm soát truy cập phù hợp. Các triển khai MCP phải ngăn chặn truyền dữ liệu trái phép và đảm bảo quyền riêng tư được duy trì trong toàn bộ tương tác.

- **An toàn công cụ**: Trước khi gọi bất kỳ công cụ nào, cần có sự đồng ý rõ ràng từ người dùng. Người dùng cần hiểu rõ chức năng của từng công cụ, và các ranh giới bảo mật vững chắc phải được thực thi để ngăn chặn thực thi công cụ không mong muốn hoặc không an toàn.

Tuân thủ các nguyên tắc này, MCP đảm bảo niềm tin, quyền riêng tư và an toàn của người dùng được duy trì xuyên suốt các tương tác protocol.

## Ví dụ mã: Các thành phần chính

Dưới đây là các ví dụ mã trong một số ngôn ngữ lập trình phổ biến minh họa cách triển khai các thành phần server MCP và công cụ.

### Ví dụ .NET: Tạo MCP Server đơn giản với công cụ

Đây là ví dụ mã .NET thực tế cho thấy cách triển khai một MCP server đơn giản với các công cụ tùy chỉnh. Ví dụ này trình bày cách định nghĩa và đăng ký công cụ, xử lý yêu cầu, và kết nối server sử dụng Model Context Protocol.

```csharp
using System;
using System.Threading.Tasks;
using ModelContextProtocol.Server;
using ModelContextProtocol.Server.Transport;
using ModelContextProtocol.Server.Tools;

public class WeatherServer
{
    public static async Task Main(string[] args)
    {
        // Create an MCP server
        var server = new McpServer(
            name: "Weather MCP Server",
            version: "1.0.0"
        );
        
        // Register our custom weather tool
        server.AddTool<string, WeatherData>("weatherTool", 
            description: "Gets current weather for a location",
            execute: async (location) => {
                // Call weather API (simplified)
                var weatherData = await GetWeatherDataAsync(location);
                return weatherData;
            });
        
        // Connect the server using stdio transport
        var transport = new StdioServerTransport();
        await server.ConnectAsync(transport);
        
        Console.WriteLine("Weather MCP Server started");
        
        // Keep the server running until process is terminated
        await Task.Delay(-1);
    }
    
    private static async Task<WeatherData> GetWeatherDataAsync(string location)
    {
        // This would normally call a weather API
        // Simplified for demonstration
        await Task.Delay(100); // Simulate API call
        return new WeatherData { 
            Temperature = 72.5,
            Conditions = "Sunny",
            Location = location
        };
    }
}

public class WeatherData
{
    public double Temperature { get; set; }
    public string Conditions { get; set; }
    public string Location { get; set; }
}
```

### Ví dụ Java: Thành phần MCP Server

Ví dụ này thể hiện cùng MCP server và đăng ký công cụ như ví dụ .NET ở trên, nhưng được triển khai bằng Java.

```java
import io.modelcontextprotocol.server.McpServer;
import io.modelcontextprotocol.server.McpToolDefinition;
import io.modelcontextprotocol.server.transport.StdioServerTransport;
import io.modelcontextprotocol.server.tool.ToolExecutionContext;
import io.modelcontextprotocol.server.tool.ToolResponse;

public class WeatherMcpServer {
    public static void main(String[] args) throws Exception {
        // Create an MCP server
        McpServer server = McpServer.builder()
            .name("Weather MCP Server")
            .version("1.0.0")
            .build();
            
        // Register a weather tool
        server.registerTool(McpToolDefinition.builder("weatherTool")
            .description("Gets current weather for a location")
            .parameter("location", String.class)
            .execute((ToolExecutionContext ctx) -> {
                String location = ctx.getParameter("location", String.class);
                
                // Get weather data (simplified)
                WeatherData data = getWeatherData(location);
                
                // Return formatted response
                return ToolResponse.content(
                    String.format("Temperature: %.1f°F, Conditions: %s, Location: %s", 
                    data.getTemperature(), 
                    data.getConditions(), 
                    data.getLocation())
                );
            })
            .build());
        
        // Connect the server using stdio transport
        try (StdioServerTransport transport = new StdioServerTransport()) {
            server.connect(transport);
            System.out.println("Weather MCP Server started");
            // Keep server running until process is terminated
            Thread.currentThread().join();
        }
    }
    
    private static WeatherData getWeatherData(String location) {
        // Implementation would call a weather API
        // Simplified for example purposes
        return new WeatherData(72.5, "Sunny", location);
    }
}

class WeatherData {
    private double temperature;
    private String conditions;
    private String location;
    
    public WeatherData(double temperature, String conditions, String location) {
        this.temperature = temperature;
        this.conditions = conditions;
        this.location = location;
    }
    
    public double getTemperature() {
        return temperature;
    }
    
    public String getConditions() {
        return conditions;
    }
    
    public String getLocation() {
        return location;
    }
}
```

### Ví dụ Python: Xây dựng MCP Server

Trong ví dụ này, chúng tôi trình bày cách xây dựng MCP server bằng Python. Bạn cũng được chỉ ra hai cách khác nhau để tạo công cụ.

```python
#!/usr/bin/env python3
import asyncio
from mcp.server.fastmcp import FastMCP
from mcp.server.transports.stdio import serve_stdio

# Create a FastMCP server
mcp = FastMCP(
    name="Weather MCP Server",
    version="1.0.0"
)

@mcp.tool()
def get_weather(location: str) -> dict:
    """Gets current weather for a location."""
    # This would normally call a weather API
    # Simplified for demonstration
    return {
        "temperature": 72.5,
        "conditions": "Sunny",
        "location": location
    }

# Alternative approach using a class
class WeatherTools:
    @mcp.tool()
    def forecast(self, location: str, days: int = 1) -> dict:
        """Gets weather forecast for a location for the specified number of days."""
        # This would normally call a weather API forecast endpoint
        # Simplified for demonstration
        return {
            "location": location,
            "forecast": [
                {"day": i+1, "temperature": 70 + i, "conditions": "Partly Cloudy"}
                for i in range(days)
            ]
        }

# Instantiate the class to register its tools
weather_tools = WeatherTools()

# Start the server using stdio transport
if __name__ == "__main__":
    asyncio.run(serve_stdio(mcp))
```

### Ví dụ JavaScript: Tạo MCP Server

Ví dụ này cho thấy cách tạo MCP server bằng JavaScript và cách đăng ký hai công cụ liên quan đến thời tiết.

```javascript
// Using the official Model Context Protocol SDK
import { McpServer } from "@modelcontextprotocol/sdk/server/mcp.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { z } from "zod"; // For parameter validation

// Create an MCP server
const server = new McpServer({
  name: "Weather MCP Server",
  version: "1.0.0"
});

// Define a weather tool
server.tool(
  "weatherTool",
  {
    location: z.string().describe("The location to get weather for")
  },
  async ({ location }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const weatherData = await getWeatherData(location);
    
    return {
      content: [
        { 
          type: "text", 
          text: `Temperature: ${weatherData.temperature}°F, Conditions: ${weatherData.conditions}, Location: ${weatherData.location}` 
        }
      ]
    };
  }
);

// Define a forecast tool
server.tool(
  "forecastTool",
  {
    location: z.string(),
    days: z.number().default(3).describe("Number of days for forecast")
  },
  async ({ location, days }) => {
    // This would normally call a weather API
    // Simplified for demonstration
    const forecast = await getForecastData(location, days);
    
    return {
      content: [
        { 
          type: "text", 
          text: `${days}-day forecast for ${location}: ${JSON.stringify(forecast)}` 
        }
      ]
    };
  }
);

// Helper functions
async function getWeatherData(location) {
  // Simulate API call
  return {
    temperature: 72.5,
    conditions: "Sunny",
    location: location
  };
}

async function getForecastData(location, days) {
  // Simulate API call
  return Array.from({ length: days }, (_, i) => ({
    day: i + 1,
    temperature: 70 + Math.floor(Math.random() * 10),
    conditions: i % 2 === 0 ? "Sunny" : "Partly Cloudy"
  }));
}

// Connect the server using stdio transport
const transport = new StdioServerTransport();
server.connect(transport).catch(console.error);

console.log("Weather MCP Server started");
```

Ví dụ JavaScript này trình bày cách tạo MCP client kết nối tới server, gửi prompt, và xử lý phản hồi bao gồm các cuộc gọi công cụ được thực hiện.

## Bảo mật và ủy quyền

MCP bao gồm một số khái niệm và cơ chế tích hợp để quản lý bảo mật và ủy quyền xuyên suốt protocol:

1. **Kiểm soát quyền công cụ**:  
  Clients có thể chỉ định công cụ nào mô hình được phép sử dụng trong phiên làm việc. Điều này đảm bảo chỉ các công cụ được ủy quyền rõ ràng mới có thể truy cập, giảm rủi ro thao tác không mong muốn hoặc không an toàn. Quyền có thể được cấu hình động dựa trên sở thích người dùng, chính sách tổ chức hoặc ngữ cảnh tương tác.

2. **Xác thực**:  
  Servers có thể yêu cầu xác thực trước khi cấp quyền truy cập công cụ, tài nguyên hoặc thao tác nhạy cảm. Điều này có thể bao gồm khóa API, token OAuth hoặc các cơ chế xác thực khác. Xác thực đúng giúp đảm bảo chỉ clients và người dùng đáng tin cậy mới có thể gọi các chức năng server.

3. **Kiểm tra hợp lệ**:  
  Việc kiểm tra tham số được thực thi cho tất cả các cuộc gọi công cụ. Mỗi công cụ định nghĩa loại, định dạng và giới hạn tham số mong đợi, và server kiểm tra các yêu cầu đến tương ứng. Điều này ngăn chặn dữ liệu đầu vào sai hoặc độc hại ảnh hưởng tới việc thực thi công cụ và duy trì tính toàn vẹn hoạt động.

4. **Giới hạn tốc độ**:  
  Để ngăn ngừa lạm dụng và đảm bảo sử dụng tài nguyên server công bằng, MCP servers có thể áp dụng giới hạn tốc độ cho các cuộc gọi công cụ và truy cập tài nguyên. Giới hạn có thể áp dụng theo người dùng, phiên làm việc hoặc toàn hệ thống, giúp bảo vệ chống tấn công từ chối dịch vụ hoặc sử dụng tài nguyên quá mức.

Kết hợp các cơ chế này, MCP cung cấp nền tảng bảo mật vững chắc cho việc tích hợp mô hình ngôn ngữ với công cụ và nguồn dữ liệu bên ngoài, đồng

**Tuyên bố từ chối trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ gốc nên được coi là nguồn chính xác và đáng tin cậy. Đối với các thông tin quan trọng, nên sử dụng dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.