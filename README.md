## lab4
# Ex2_name_OR.v
module Ex2_OR(x1, x2, f);
    input x1, x2;
    output f;
    assign f = (x1 & ~x2) | (~x1 & x2);
endmodule

# Stimul.do
force x1 2'b0 0ns, 2'b1 100ns;
force x2 2'b0 0ns, 2'b1 50ns, 2'b0 100ns, 2'b1 150ns;

# f4_ddnf.v

module f4_ddnf(x1, x2, x3, f);
    input x1, x2, x3;
    output f;
    wire term1, term2;
    assign term1 = ~x3 & ~x2 & ~x1;
    assign term2 = x2 & x1;
    assign f = term1 | term2;
endmodule

# f4_dknf.v

module f4_dknf(x1, x2, x3, f);
    input x1, x2, x3;
    output f;
    wire t1, t2, t3, t4, t5;
    assign t1 = x3 | ~x2 | x1;
    assign t2 = x3 | x2 | ~x1;
    assign t3 = ~x3 | x2 | x1;
    assign t4 = ~x3 | ~x2 | x1;
    assign t5 = ~x3 | ~x2 | ~x1;
    assign f = t1 & t2 & t3 & t4 & t5;
endmodule

# f4_stim.do

force x1 2'b0 0ns, 2'b1 10ns, 2'b0 20ns, 2'b1 30ns, 2'b0 40ns, 2'b1 50ns, 2'b0 60ns, 2'b1 70ns;
force x2 2'b0 0ns, 2'b0 10ns, 2'b1 20ns, 2'b1 30ns, 2'b0 40ns, 2'b0 50ns, 2'b1 60ns, 2'b1 70ns;
force x3 2'b0 0ns, 2'b0 10ns, 2'b0 20ns, 2'b0 30ns, 2'b1 40ns, 2'b1 50ns, 2'b1 60ns, 2'b1 70ns;
