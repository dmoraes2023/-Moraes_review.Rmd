# Peer review- March 15, 2024- Daniel Moraes
# Data Inspection and Processing

Line86-88: I liked the command. It gives a good summary for the genotypes by group
> summary(as.factor(maizegenotypes$Group))
Overall, your data is very well organized. I do not have any additional suggestions.
# Data visualization
Overall, your plots look great. I have few suggestions:
Data visualization: You can create a folder as plots as you did in Line 164-167; dir.create('./your foldername')
Then, you can save as tiff format and also export to github. For example, from your first plot in Line 222:
# Your code is:
ggplot(cmergedfiles) + geom_bar(aes(x = Chromosome, fill = Chromosome)) + scale_fill_manual(values = rainbow(length(levels(cmergedfiles$Chromosome)))) + xlab("Chromosome") + ylab("AllTotal SNPs")
# My suggestion is:
Snps_counts <- ggplot(cmergedfiles) + geom_bar(aes(x = Chromosome, fill = Chromosome)) + scale_fill_manual(values = rainbow(length(levels(cmergedfiles$Chromosome)))) + xlab("Chromosome") + ylab("AllTotal SNPs")
Then, to save as tiff:
ggsave("Snps_counts.tiff", plot = Snps_counts, device = "tiff", width = 8, height = 6, units = "in")

# Finally, your own visualization graph looks great. Here is a suggestion for a visualization option:
# Your code is:
ggplot(mergedfiles) +
  geom_count(aes(x = Chromosome, y = gene_count)) +
   xlab("Chromosomes") +
  ylab("Count of Genes")

# My suggestion is:
Plot <- ggplot(mergedfiles) +
  geom_count(aes(x = Chromosome, y = gene_count)) +
  xlab("Chromosomes") +
  ylab("Count of Genes") +
  theme_bw() +
  labs(y = "Count of Genes", x = "Chromosome") +
  theme(
    axis.text = element_text(size = 14),
    legend.position = "bottom",
    legend.text = element_text(size = 14),
    legend.title = element_text(size = 14),
    axis.title = element_text(size = 14)
  ) +
  ggtitle("My own visualization")
Plot
