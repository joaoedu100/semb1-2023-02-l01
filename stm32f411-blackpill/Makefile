#####################################################################
 # Makefile
 #
 #   Aluno: João Eduardo Moya - (11921EAU010)
 # 
#####################################################################
 
 
CC = arm-none-eabi-gcc

RM = rm -rf

OBJDIR = build

DEPDIR = .deps

SRCS = startup.c  main.c

CFLAGS = -g -mcpu=cortex-m4 -mthumb -Wall -O0

DEPFLAGS = -MMD -MP -MF $(DEPDIR)/$*.d

OBJS = $(patsubst %, $(OBJDIR)/%.o, $(basename $(SRCS)))
DEPS = $(patsubst %, $(DEPDIR)/%.d, $(basename $(SRCS)))

$(shell mkdir -p $(dir $(OBJS)) > /dev/null)
$(shell mkdir -p $(dir $(DEPS)) > /dev/null)

all: $(OBJS)

$(OBJDIR)/%.o: %.c $(DEPDIR)/%.d
	$(CC) -c $(CFLAGS) $(DEPFLAGS) $< -o $@

$(DEPS):

-include $(DEPS)

.PHONY: clean
clean:
	$(RM) $(OBJDIR) $(DEPDIR)
