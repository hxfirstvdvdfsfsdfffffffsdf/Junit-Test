# Junit-Test
单元测试学习
```
package com.zzb.generator;
import static org.junit.Assert.assertTrue;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.AutoConfigureMockMvc;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.http.MediaType;
import org.springframework.test.context.ActiveProfiles;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.test.web.servlet.MvcResult;
@SpringBootTest
@ActiveProfiles(profiles = "dev")
@AutoConfigureMockMvc
public class MochitoTest {
@Autowired
private MockMvc mvc;
	@Test
	public void test1() throws Exception{
		MvcResult  result=mvc.perform(get("/hi")
				.param("param", "xixixi")
				.contentType(MediaType.APPLICATION_JSON))
				   .andExpect(status().isOk())
				  // .andExpect(jsonPath("param", is("xixixi")))
				   	.andReturn();
		assertTrue("hixixixi".equals(result.getResponse().getContentAsString()));
		System.out.println(result.getResponse().getContentAsString());			
	}
}
```
