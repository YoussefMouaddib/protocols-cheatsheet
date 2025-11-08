# Verilog AXI Templates (Reusable Patterns)

## AXI-Lite Slave Skeleton
always @(posedge clk) begin
    if (reset) begin
        // reset signals
    end else begin
        if (awvalid && awready) addr_reg <= awaddr;
        if (wvalid && wready)   data_reg <= wdata;

        if (write_fire)
            register_file[addr_reg] <= data_reg;

        if (read_fire)
            rdata <= register_file[araddr];
    end
end

## AXI Read/Write Fire Conditions
wire write_fire = awvalid && awready && wvalid && wready;
wire read_fire  = arvalid && arready;

## AXIS Handshake
assign tready = fifo_not_empty;
assign fifo_pop = tvalid && tready;
